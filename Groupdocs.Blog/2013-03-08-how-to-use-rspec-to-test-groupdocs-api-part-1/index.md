---
title: 'How to Use RSpec to Test GroupDocs API? - Part 1'
date: Fri, 08 Mar 2013 10:15:54 +0000
draft: false
url: /2013/03/08/how-to-use-rspec-to-test-groupdocs-api-part-1/
author: 'Derek Hyland'
summary: ''
tags: ['API', 'document management', 'document upload', 'online document management system', 'zArchive']
---

In this article, we will review how to use Ruby RSpec for testing REST APIs like GroupDocs. RSpec is a BDD (behavior driven development) framework. You can find more info about RSpec on [its official site](http://rspec.info/). There are a lot of different [GroupDocs APIs](http://api.groupdocs.com/v2.0/spec/) that you can use. In this article we will test one of the User APIs: "Get user profile".

## What You NeedYou need Ruby, Gem, Bundler, and RSpec (gem install rspec) installed on you computer. You also need a GroupDocs account and private and client keys. [Find out how to get GroupDocs API keys](https://docs.groupdocs.cloud/total/create-new-app-and-get-app-key-and-sid/).

## Getting StartedFirst of all, create a folder for future tests (for example groupdocs\_tests) and create file with the name **Gemfile** with the following content:```
source 'https://rubygems.org'

gem 'rake'
gem 'rspec'
gem 'ci\_reporter'
gem 'groupdocs'
```Here we define all gems that we will need for API testing. The first line defines the source for gems. Then, we list the gems we're using:

*   gem 'rake'  - a build tool for Ruby.
*   gem 'rspec' - a BDD testing framework.
*   gem 'ci\_reporter' - an add-on to Test::Unit and RSpec that allows you to generate XML reports of your test and/or spec runs.
*   gem 'groupdocs' - the GroupDocs Ruby SDK.

After adding the **Gemfile** file, you need to use the bundle and install all required gems. We will install gems locally by commands in a terminal. Make sure that you are in the groupdocs\_tests directory:

```
bundle install --path vendor/bundle
```

## Creating Test FoldersNow we will create additional folders for our test:

1.  In the test's root directory (**groupdocs\_tests**), create a **spec** folder. All Ruby project tests should be in the **spec** folder.
2.  In the **spec** folder, create a **user** folder. As we will test the User API we will put all our User test in this folder

## Writing the CodeNow let's write some Ruby code.

1.  Create a **spec\_helper.rb** file in the **spec/** folder. We will use this file to configure the GroupDocs SDK and for some helpers.
2.  Create a **get\_user\_profile\_spec.rb** file in the **user/** folder. Specs files name should ends with the "\_spec" suffix. "get\_user\_profile" is the name of the API that we will test.

### /groupdocs\_tests/spec/spec\_helper.rb content```
require 'groupdocs'

RSpec.configure do |spec|

  # configure API access
  GroupDocs.configure do |groupdocs|
    groupdocs.api\_server  = "https://api.groupdocs.com"
    groupdocs.api\_version = "2.0"
    groupdocs.client\_id   = '' #your Client ID here
    groupdocs.private\_key = '' #your Private Key here
  end

  # share API tests methods
  spec.shared\_context :api\_tests do
    let(:response) do |spec|
      response = request.execute!
    end
  end

end
```

### /groupdocs\_tests/spec/user/get\_user\_profile\_spec.rb content```
require 'spec\_helper'

describe 'User' do
  describe 'GetUserProfile' do
    include\_context :api\_tests

    let(:request) do
      GroupDocs::Api::Request.new method: 'GET',
                                  path:   '/mgmt/{{client\_id}}/profile'
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
```Enter your keys and email where it needed. That's all you need to do.

## Running the TestMake sure that your test work fine, in terminal:

```
rspec spec/user/get\_user\_profile\_spec.rb
```

If everything is fine, you will see something like this: ![](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/03/1.png "1")

## Coming UpIn the next part, we will see how to test an API with the "POST" and "PUT" methods:

*   What is expectation (should and should\_not) and how do we use them?
*   What is matchers and how do we use them?




