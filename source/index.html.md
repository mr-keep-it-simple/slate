---
title: enjine.io - CloudStore

language_tabs: # must be one of https://git.io/vQNgJ
  - javascript

toc_footers:
  - <a href='mailto:support@droidscript.org'>Sign Up for a CloudStore API Key</a>
  #- <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true

code_clipboard: true

code_run: true
---

# CloudStore
```javascript
//Called when application is started.
function OnStart()
{
	//Create a layout with objects vertically centered.
	lay = app.CreateLayout( "linear", "VCenter,FillXY" );	

	//Add a button to save settings to cloud.
	btnSave = app.AddButton( lay, "Save", 0.3, 0.1 );
	btnSave.SetOnTouch( btnSave_OnTouch );
	
	//Add a button to load settings from cloud.
	btnLoad = app.AddButton( lay, "Load", 0.3, 0.1 );
	btnLoad.SetMargins( 0, 0.05, 0, 0 );
	btnLoad.SetOnTouch( btnLoad_OnTouch );
	
	//Add layout to app.	
	app.AddLayout( lay );
	
	//Create CloudStore component.
	//(Note: this is a dummy key and will show an error)
	cloud = app.CreateCloudStore( <YOUR_CLOUDSTORE_KEY> )
}

//Called when user touches our Save button.
function btnSave_OnTouch()
{	
	cloud.Save( "GreenHouse", {"Humidity":88,"Temp":27}, OnSave )
}

//Called when the cloud save has completed.
function OnSave( error, response, status )
{
    if( error ) app.ShowPopup( "Http Error: " + response + " " + status )
    else if( response.error ) app.ShowPopup( "CloudStore Error: " + response.error )
    else app.ShowPopup( response.data );
}

//Called when user touches our Save button.
function btnLoad_OnTouch()
{
	cloud.Load( "GreenHouse", OnLoad )
}

//Called when the cloud save has completed.
function OnLoad( error, response, status )
{
    if( error ) app.ShowPopup( "Http Error: " + response + " " + status )
    else if( response.error ) app.ShowPopup( "CloudStore Error: " + response.error )
    else app.ShowPopup( response.data.Humidity );
}

```
> Make sure to replace `<YOUR_CLOUDSTORE_KEY>` with your CloudStore key.

The CloudStore feature is a [Premium](mailto:support@droidscript.org) only service.

CloudStore allows you to read and write data to the cloud using your CloudStore [key](https://enjine.io).

This feature allows you to save data outside of your app, making it possible to share information between multiple apps.

It also means you can keep data seperate and persistent from your app.  So if you remove or change an app in anyway your data is preserved. 

CloudStore uses API keys to allow access to the CloudStore service. You can register a new CloudStore key at our [enjine.io portal](https://enjine.io).

<aside class="notice">
You must replace <code>&lt;YOUR_CLOUDSTORE_KEY&gt;</code> with your personal CloudStore key.
</aside>

## Store data

`cloud.Save( KEY, VALUE, CALLBACK )`

### Query Parameters
Parameter | Required | Description
--------- | ------- | -----------
KEY | true | A string id to identify the data to store
VALUE | true | The data to store.  You can store a string, integer, or even a JavaScript object 
CALLBACK | false | A function with 3 parameters: error, response, status

## Get data

`cloud.Load( KEY, CALLBACK )`

### Query Parameters
Parameter | Required | Description
--------- | ------- | -----------
KEY | true | A string id to identify the data to store
CALLBACK | false | A function with 3 parameters: error, response, status.  If the response if OK, you can access the data through response.data



<!--
<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>


<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>
-->
