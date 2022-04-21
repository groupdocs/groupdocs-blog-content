---
title: 'Working with Groupdocs Signature API from Ruby'
date: Mon, 11 Feb 2013 11:34:56 +0000
draft: false
url: /2013/02/11/working-with-groupdocs-signature-api-from-ruby/
author: 'Derek Hyland'
summary: ''
tags: ['API', 'digital signature', 'electronic signature', 'esignature', 'GroupDocs Signature', 'zArchive']
---

Today we will find out how to use GroupDocs' Ruby SDK. We will create a GroupDocs Signature envelope sample with the Sinatra framework. GroupDocs Signature envelopes are used to prepare documents for digital signature and managing the signature process.

## Setting UpFirst, create the application folders structure:

*   your\_app/public – for CSS files.
*   your\_app/samples – for sample files.
*   your\_app/views – for view files, we will use Haml for these.

Also we need to create a Gemfile in our project's root directory with the following content: [https://gist.github.com/averjr/4739176](https://gist.github.com/averjr/4739176)

## Writing the ApplicationLets start our application. Create app.rb file with following content: [https://gist.github.com/averjr/4739208](https://gist.github.com/averjr/4739208)

*   Lines 1-3 requires the Sinatra framework, GroupDocs SDK and haml for our views.
*   Lines 5-7 creates our first root with a view named index.haml. By default, Sinatra looks for view files in views directory.
*   Line 13 includes all Ruby files from the samples directory.

Now lets work on the views. Create a parent layout file called layout.haml. [https://gist.github.com/averjr/a0313da572e3141811f3](https://gist.github.com/averjr/a0313da572e3141811f3) It is really easy to work with HTML using Haml. Find out more about Haml. Here's anonline tool for converting HTML to Haml. Note that in Haml, you don't have to close tags and indents are very important! “= yield” is where child templates are included. In index.haml you'll see an h1 header, div container and ul list with one list element that links to our envelope sample: [https://gist.github.com/averjr/c23ab36e0b8e3415dc8e](https://gist.github.com/averjr/c23ab36e0b8e3415dc8e) You can add any HTML attribute like this: {:your\_attribute => “your attribute value”}.

## The Starting PointBefore creating the envelope sample, lets look at what we have. To avoid problems with starting the application, use rvm. ([This article explains how to install rvm](https://rvm.io/rvm/install).) Now install a local bundle by typing this command in a terminal, while in the app directory:

```
 gem install bundler
```

If it is installed already, use this command:

```
bundle install --path vendor/bundle
```

And now you could start the application:

```
 bundle exec ruby app.rb
```

In the terminal, you will see something like this: \[caption id="attachment\_1501" align="aligncenter" width="535" caption="Terminal - Terminal massages after starting Sinatra server"\]![Terminal - Terminal massages after starting Sinatra server](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/02/Terminal-massages-after-starting-Sinatra-server.png "Terminal - Terminal massages after starting Sinatra server")\[/caption\] Open in you browser with the URL **http://localhost:4567/** and you will see the following: \[caption id="attachment\_1502" align="aligncenter" width="409" caption="Index page - Index page of our app without CSS"\]![Index page - Index page of our app without CSS](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/02/Index-page-Index-page-of-our-app-without-CSS.png "Index page - Index page of our app without CSS")\[/caption\] Add a little CSS in public/css directory: [https://gist.github.com/averjr/4752864](https://gist.github.com/averjr/4752864) Re-load the page and you will see: \[caption id="attachment\_1503" align="aligncenter" width="705" caption="Index page with CSS - After adding CSS the page looks like this"\]![Index page with CSS - After adding CSS the page looks like this](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/02/Index-page-with-CSS-After-adding-CSS-the-page-looks-like-this.png "Index page with CSS - After adding CSS the page looks like this")\[/caption\]

## Creating the Envelope ExampleLets create envelope\_sample.haml in your views directory with the following content:[https://gist.github.com/averjr/4739266](https://gist.github.com/averjr/4739266) We have created a form that sends the ClientID, PrivateKey and the file to be signed. Now write the Ruby code that handles the get and post request as the file envelope-sample.rb in samples directory: [https://gist.github.com/averjr/4739271](https://gist.github.com/averjr/4739271) We have created one GET and one POST request.

## Extending the POST RequestLets extend post request and use the GroupDocs API: 1. Configuring GroupDocs SDK.

```
 GroupDocs.configure do |groupdocs|
   groupdocs.client\_id = params\[:client\_id\]
   groupdocs.private\_key = params\[:private\_key\]
   groupdocs.api\_server = 'https://stage-api.groupdocs.com'
 end
```

2\. Upload document.

```
 filepath = "#{Dir.tmpdir}/#{params\[:file\]\[:filename\]}"
 File.open(filepath, 'wb') { |f| f.write(params\[:file\]\[:tempfile\].read) }
 file = GroupDocs::Storage::File.upload!(filepath, {}, client\_id: settings.client\_id,
 private\_key: settings.private\_key)
 document = file.to\_document
```

3\. Create envelope.

```
 envelope = GroupDocs::Signature::Envelope.new
 envelope.name = "Envelope"
 envelope.email\_subject = "Sing this!"
 envelope.create!
```

4\. Add document to envelope.

```
    envelope.add\_document! document
```

5\. Update document object after it's created.

```
    document = envelope.documents!.first
```

6\. Add new recipient to envelope.

```
 roles = GroupDocs::Signature::Role.get!
 recipient = GroupDocs::Signature::Recipient.new
 recipient.email = 'john@smith.com'
 recipient.first\_name = 'John'
 recipient.last\_name = 'Smith'
 recipient.role\_id = roles.detect { |role| role.name == "Signer" }.id
 envelope.add\_recipient! recipient
```

7\. Update recipient object after it's created.

```
    recipient = envelope.recipients!.first
```

8 (Optional).  By default, fields for signing are created automatically, but you can add fields manually.

```
 # add city field to envelope
 field = GroupDocs::Signature::Field.get!.detect { |f| f.type == :single\_line }
 field.name = 'City'    field.location = { location\_x: 0.3, location\_y: 0.2, page: 1 }
 envelope.add\_field! field, document, recipient

 # add signature field to envelope
 field = GroupDocs::Signature::Field.get!.detect { |f| f.type == :signature }
 field.location = { location\_x: 0.3, location\_y: 0.3, page: 1 }
 envelope.add\_field! field, document, recipient
```

9\. Send envelope with callback URL.

```
    webhook = 'http://groupdocs-ruby-samples.herokuapp.com/envelope-sample/sign'
    envelope.send! webhook
```

10\. Construct embedded signature URL for views.

```
 url = "https://stage-apps.groupdocs.com/signature/signembed/#{envelope.id}/#{recipient.id}"
 iframe = "<iframe src='#{url}' frameborder='0' width='720' height='600'></iframe>"
```

11\. Add local vars for the view.

```
haml :envelope\_sample, :locals => { :client\_id => settings.client\_id, :private\_key => settings.private\_key,
:err => err, :iframe => iframe}
```

12\. Add code for handling exeptions.

```
  begin
    raise "Please enter all required parameters" if settings.client\_id.empty? or settings.private\_key.empty?
      ....
  rescue Exception => e
    err = e.message
  end
```

## Handling a CallbackLets handle the callback: 1. First, wait for callback and create a text file with parameters that the server sent to us:

```
post '/envelope-sample/sign' do
  # Content Type of callback is application/json
  data = JSON.parse(request.body.read)
  begin
    raise "Empty params!" if data.empty?
    #create empty file and write data as "key: value" to it
    outFile = File.new("signed", "w")
    data.each do |key, value|
      outFile.write("#{key}: #{value} \\n")
    end
    outFile.close
  rescue Exception => e
    err = e.message
  end
end
```

2\. We can also wait for a callback and download the signed envelope as ZIP file.

```
post '/envelope-sample/sign-and-download' do
  data = JSON.parse(request.body.read)
  begin
    raise "Empty params!" if data.empty?
    GroupDocs.configure do |groupdocs|
        groupdocs.client\_id = '' # Your client Client ID here
        groupdocs.private\_key = '' # Your API Key here
        groupdocs.api\_server = 'https://api.groupdocs.com'
    end
    data.each do |key, value|
      if key == 'SourceId'
        # Create envelop with id and name as SourceId parameter from callback
        envelope = GroupDocs::Signature::Envelope.new id: value,
                                                    name: value
        # download signed documents as archive
        envelope.signed\_documents! '.'
      end
    end
  rescue Exception => e
    err = e.message
  end
end
```

3\. Create route to check if callback was sent:

```
get '/envelope-sample/check' do
  if File.exist?('signed')
    File.readlines('signed').each do |line|
    end
  else
    'Have not signed yet'
  end
end
```

Check the file that was created in /envelope-sample/sign

## The Complete CodeThe final code of the sample looks like this: [https://gist.github.com/averjr/4739332](https://gist.github.com/averjr/4739332)




