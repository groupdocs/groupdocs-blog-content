---
title: 'How to use rspec to test GroupDocs API - Part 2'
date: Fri, 15 Mar 2013 14:25:17 +0000
draft: false
url: /2013/03/15/how-to-use-rspec-to-test-groupdocs-api-part-2/
author: 'Derek Hyland'
summary: ''
tags: ['API', 'document management', 'GroupDocs API', 'GroupDocs API SDK', 'online document management system', 'zArchive']
---

In the first article, [How to use rspec to test GroupDocs API. Part 1](https://blog.groupdocs.com/how-to-use-rspec-to-test-groupdocs-api-part-1), we created first test for GroupDocs API. This article describes in details how tests works, what expectation and matchers are, and how to test an API with the PULL method.

## Expectation and MatchersSo what are expectation and matchers? Lets look at a small example:

```
string ="GroupDocs"
string.should have(9).characters
string.should\_not have(5).characters
```

*   **Expectations** are defined by should and the negative form should\_not.
*   **Matchers** are defined by have(9).characters and have(5).characters.

I should also mention that spec (specification) is a description of how some part of your application should work (in our case, one of the GroupDocs API methods). Lets take the **get\_user\_profile\_spec.rb** file that we created in the last article and describe what that code is doing.

```
require 'spec\_helper'

describe 'User' do
  describe 'GetUserProfile' do
    include\_context :api\_tests

    let(:request) do
      GroupDocs::Api::Request.new method: 'GET',
                                  path:   '/mgmt/{{client\_id}}/profile'
    end

    it 'returns not empty user hash' do
      response\[:user\].should\_not be\_empty
    end

    it 'returns user identifier' do
      response\[:user\]\[:id\].should be\_a(Fixnum)
    end

    it 'returns user primary email' do
      response\[:user\]\[:primary\_email\].should == "" # your primary email here
    end

    it 'returns user private key' do
      response\[:user\]\[:pkey\].should == "" # your private key here
    end

  end
end
```

We use require 'spec\_helper' to include some configuration and helper functions. The describe method creates a group. This method could be nested with others like in the code: we're testing the GetUserProfile method, a part of User API. Sometimes you'll see the context method. This is just an alias for describe. The two methods have no functional difference, instead the difference is contextual to make tests more understandable.

### Example of simple GroupCreate a file called sample\_spec.rb with the following code:

```
describe "something" do
  it "does something" do
  end
end
```

Run the following command in a console: rspec sample\_spec.rb -fn You'll get something like this: ![](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/03/Terminal.png "Terminal")

### Different Types of MatchersNow lets find what kinds of matchers there are. In the **get\_user\_profile\_spec.rb**, when we test a response from the server we use a separate it block for each parameter we want to check. We use only 3 of all possible matchers: be\_empty, be\_a(), == . For your tests you can use: Test validity and existance:

```
be\_true - check is true (not nil or false)
be\_false - check is false (nil or false)
be\_nil - check is nil
```

Test error raising:

```
expect { ... }.to raise\_error
expect { ... }.to raise\_error(ErrorClass)
expect { ... }.to raise\_error("message")
expect { ... }.to raise\_error(ErrorClass, "message")
```

There are a lot of other built-in matchers in rspec. You can find [a full list online](https://www.relishapp.com/rspec/rspec-expectations/docs/built-in-matchers). If you need some special functionality you can create you own matchers.

## Adding a TestNow lets add one more test for the UpdateUserProfile API method. We will use the PUT method and **json** file for parameters. In the **user** folder, create a file called **update\_user\_profile\_spec.rb** with the following content:

```
require 'spec\_helper'

describe 'User' do
  describe 'UpdateUserProfile' do
    include\_context :api\_tests

    let(:payload) { payload\_file(:update\_user\_profile) }

    let(:request) do
      GroupDocs::Api::Request.new method: 'PUT',
                                  path:   "/mgmt/#{payload\[:guid\]}/profile",
                                  request\_body: payload
    end

    it 'returns response array' do
      response.should\_not be\_empty
    end

  end
end
```

### payload\_fileHere we use one new function, payload\_file. We need to add it to our **spec\_helper.rb** file where it will look like this:

```
require 'groupdocs'
require 'json'

#
# Parses payload JSON file.
#
# @param \[String\] filename
# @return \[Hash\]
#
def payload\_file(filename)
  file = File.read("#{File.dirname(\_\_FILE\_\_)}/../payload/#{filename}.json")
  JSON.parse(file, symbolize\_names: true)
end

RSpec.configure do |spec|

  # configure API access
  GroupDocs.configure do |groupdocs|
    groupdocs.api\_server  = "https://api.groupdocs.com"
    groupdocs.api\_version = "2.0"
    groupdocs.client\_id   = ''
    groupdocs.private\_key = ''
  end

  # share API tests methods
  spec.shared\_context :api\_tests do
    let(:response) do |spec|
      response = request.execute!
    end
  end

end
```

### update\_user\_profile.jsonNow all we need to do, is create a **update\_user\_profile.json** file in the paylod directory (**/groupdocs\_tests/paylod/update\_user\_profile.json**):

```
{
        "nickname": "someemail@groupdocs.com",
        "firstname": "firstname",
        "lastname": "lastname",

        "pswd\_salt": "XWeSDIKH4vDc0StcdNhGCg==",
        "signedupOn": 1358920966590,
        "signedinOn": 1358920786590,
        "signin\_count": 1,
        "roles": \[
          {
            "id": 2,
            "name": "Admin"
          }
        \],
        "id": 452,
        "guid": "6dac05617fbfwer",
        "primary\_email": "someemail@groupdocs.com"
}
```

You need to provide your own parameters in the **update\_user\_profile.json** file. Now just enter this command in a terminal:

```
bundle exec rspec spec/user/update\_user\_profile\_spec.rb
```

![](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/03/Warning1.png "Warning")




