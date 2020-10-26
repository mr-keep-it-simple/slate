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

The CloudStore feature is a [Premium](mailto:support@droidscript.org) only service.

CloudStore allows you to read and write data to the cloud using your CloudStore [key](https://enjine.io).

This feature allows you to save data outside of your app, making it possible to share information between multiple apps.

It also means you can keep data seperate and persistent from your app.  So if you remove or change an app in anyway your data is preserved. 

# Example

> To start using CloudStore, use this code:

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

> Make sure to replace `YOUR_CLOUDSTORE_KEY` with your CloudStore key.

Kittn uses API keys to allow access to the CloudStore service. You can register a new CloudStore key at our [enjine.io portal](https://enjine.io).

<aside class="notice">
You must replace <code><YOUR_CLOUDSTORE_KEY></code> with your personal CloudStore key.
</aside>

# Tutorial

## Store data

```javascript
cloud = app.CreateCloudStore( <YOUR_CLOUDSTORE_KEY> )
cloud.Save( "GreenHouse", {"Humidity":88,"Temp":27}, OnSave )

//Called when the cloud save has completed.
function OnSave( error, response, status )
{
    if( error ) app.ShowPopup( "Http Error: " + response + " " + status )
    else if( response.error ) app.ShowPopup( "CloudStore Error: " + response.error )
    else app.ShowPopup( response.data );
}

```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all kittens.

### HTTP Request

`GET http://example.com/api/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Delete a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.delete(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.delete(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -X DELETE
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

