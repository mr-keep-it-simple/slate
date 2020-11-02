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

`cloud.Save( key, value, callback )`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
key | true | A string id to identify the data to store
value | true | The data to store.  You can store a string, integer, or even a JavaScript object 
callback | false | A function with 3 parameters: error, response, status

> <aside class="notice-right">You must replace <code>&lt;YOUR_CLOUDSTORE_KEY&gt;</code> with your personal CloudStore key.</aside>

### Example

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

## Getting data

`cloud.Load( key, callback )`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
key | true | A string id to identify the data to store
callback | false | A function with 3 parameters: error, response, status.  If the response if OK, you can access the data through response.data

### Example

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

## Merging data

`cloud.Merge( key, value, callback )`

You can merge data objects enabling you to modify and update data shared between multiple apps. The **Merge** function recursively merges values passed with the source object, replacing any existing data and adding new data.

Source properties that resolve to undefined are skipped if a destination value exists. Array and plain object properties are merged recursively. Other objects and value types are overridden by assignment. Source objects are applied from left to right. Subsequent sources overwrite property assignments of previous sources.

Parameter | Required | Description
--------- | ------- | -----------
key | true | A string id to identify the data to merge
value | true | A JavaScript data object containing the data you want to merge with the source object.  If no source object exists, a new object will be created
callback | false | An async function called when the merge has completed

### Example

#### App 1

```javascript
//Create CloudStore component.
cloud = app.CreateCloudStore( "<YOUR_CLOUDSTORE_KEY>" )

//Save some data.
cloud.Save( "GreenHouse", {"Temp":27}, OnSave )

// Process OnSave as usual...
```

#### App 2

```javascript
//Create CloudStore component.
cloud = app.CreateCloudStore( "<YOUR_CLOUDSTORE_KEY>" )

//Merge some data with our GreenHouse store and change the Temp value.
cloud.Merge( "GreenHouse", {"Humidity":88,"Temp":50}, OnSave )

//Handle the response.
function OnSave( error, response, status )
{
    if( error ) console.log( "Http Error: " + response + " " + status )
    else if( response.error ) console.log( "CloudStore Error: " + response.error )
    else {
        // Data merged successfully
        // Lets now reload the data to see if our object has changed
        cloud.Load( "GreenHouse", OnLoad )
    }
}

//Handle the response.
function OnLoad( error, response, status )
{
    if( error ) console.log( "Http Error: " + response + " " + status )
    else if( response.error ) console.log( "CloudStore Error: " + response.error )
    else console.log( response.data.Humidity );
}
```

## Deleting data

`cloud.Delete( key, callback )`

You can delete cloudstore data by sending the id of the item you wish to remove.

Parameter | Required | Description
--------- | ------- | -----------
key | true | A string id to identify the data store to delete
callback | false | An async function called when the delete has completed with success or fail

### Example

```javascript
//Create CloudStore component.
cloud = app.CreateCloudStore( "<YOUR_CLOUDSTORE_KEY>" )

cloud.Delete( "GreenHouse", OnDelete )

//Handle the response.
function OnLoad( error, response, status )
{
    if( error ) console.log( "Http Error: " + response + " " + status )
    else if( response.error ) console.log( "CloudStore Error: " + response.error )
    else console.log( "Store deleted!" );
}
```

<%= image_tag "images/logo.png" %>



<!--
<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>


<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>
-->
