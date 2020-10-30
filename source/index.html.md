---
title: enjine.io - CloudStore

language_tabs: # must be one of https://git.io/vQNgJ
  - javascript

toc_footers:
  - <a href='mailto:support@droidscript.org'>Sign Up for a CloudStore API Key</a>

includes:

search: true

code_clipboard: true

code_run: true
---

# CloudStore

CloudStore allows you to read and write data to the cloud using your CloudStore [key](https://enjine.io).

This feature allows you to save data outside of your app, making it possible to share information between multiple apps.

It also means you can keep data seperate and persistent from your app.  So if you remove or change an app in anyway your data is preserved. 

CloudStore uses API keys to allow access to the CloudStore service. You can register a new CloudStore key at our [enjine.io portal](https://enjine.io).

## Saving data

`cloud.Save( KEY, VALUE, CALLBACK )`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
KEY | true | A string id to identify the data to store
VALUE | true | The data to store.  You can store a string, integer, or even a JavaScript object 
CALLBACK | false | A function with 3 parameters: error, response, status

> <aside class="notice-right">You must replace <code>&lt;YOUR_CLOUDSTORE_KEY&gt;</code> with your personal CloudStore key.</aside>

```javascript
//Create CloudStore component.
cloud = app.CreateCloudStore( "<YOUR_CLOUDSTORE_KEY>" )

//Save some data.
cloud.Save( "GreenHouse", {"Humidity":88,"Temp":27}, OnSave )

//Handle the response.
function OnSave( error, response, status )
{
    if( error ) console.log( "Http Error: " + response + " " + status )
    else if( response.error ) console.log( "CloudStore Error: " + response.error )
    else console.log( "Data Saved: " + response.data )
}
```

## Geting data

`cloud.Load( KEY, CALLBACK )`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
KEY | true | A string id to identify the data to store
CALLBACK | false | A function with 3 parameters: error, response, status.  If the response if OK, you can access the data through response.data

```javascript
//Create CloudStore component.
cloud = app.CreateCloudStore( "<YOUR_CLOUDSTORE_KEY>" )

//Load some data.
cloud.Load( "GreenHouse", OnLoad )

//Handle the response.
function OnLoad( error, response, status )
{
    if( error ) console.log( "Http Error: " + response + " " + status )
    else if( response.error ) console.log( "CloudStore Error: " + response.error )
    else console.log( response.data.Humidity );
}
```

<%= image_tag "images/logo.png" %>



<!--
<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>


<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>
-->
