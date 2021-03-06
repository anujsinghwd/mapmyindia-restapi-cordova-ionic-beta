
# MapmyIndia REST APIs for Cordova/Ionic - Beta 1

[![N|Solid](https://www.mapmyindia.com/api/img/mapmyindia-api.png)](https://www.mapmyindia.com/api/)

For full documentation contact MapmyIndia here:

[MapmyIndia: apisupport@mapmyindia.com](mailto:apisupport@mapmyindia.com).

You can get your api key to be used in this document here: [https://www.mapmyindia.com/api/signup](https://www.mapmyindia.com/api/signup)

## Version History
| Version | Last Updated | Author |
| ---- | ---- | ---- |
| 0.0.9 | November 2018 | MapmyIndia API Team ([AS](https://github.com/anujsinghwd)) |

## Technologies Used

1.  [Java](https://www.java.com/en/download/)
2.  [Javascript](https://developer.mozilla.org/bm/docs/Web/JavaScript)
3.  [Cordova](https://cordova.apache.org/)
4.  [ObjectiveC](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/ProgrammingWithObjectiveC/Introduction/Introduction.html#//apple_ref/doc/uid/TP40011210-CH1-SW1)

  

## Supported Platform
1.  [Andoroid](https://www.android.com/)
2.  [Ios](https://www.apple.com/in/ios/)
3.  [Browser](https://www.google.com/chrome/)

 
## Supported Technologies
1.  [Ionic](https://ionicframework.com/)
2.  [Cordova](https://cordova.apache.org/)
3.  [Phonegap](https://phonegap.com/)

 
## Installation

### npm
```js
 > cordova  plugin  add  mapmyindia-restapi-cordova-ionic-beta
```

### git

```js
> cordova plugin add https://github.com/mapmyindia/mapmyindia-restapi-cordova-ionic-beta.git
```

### Browser Installation
| IONIC | CORDOVA |
| ---- | ---- |
| ionic cordova platform add browser | cordova platform add browser |

### Running in the browser
| IONIC | CORDOVA |
| ---- | ---- |
| ionic cordova run browser | cordova run browser |

 
#### Only if you are running cordova project in browser not for ionicframework
- replace your `<meta>` tag in `index.html`
	```js
	<meta  http-equiv="Content-Security-Policy"  content="default-src *; style-src 'self' http://* 'unsafe-inline'; script-src 'self' http://* 'unsafe-inline' 'unsafe-eval'" />
	```

	> MapmyIndia Plugin requires Cordova to run.

- Declare mmi_rest var globally
	```js
	> declare var mmi_rest;
	```
	> Inside `mmi_rest` function if you want to access this property you have to assign to a variable like
	>
	>  `var thisObj = this` outside the `mmi_rest` function body if you are working with `IONIC V > 1`

## API Usage

### Features:

1.  [Autosuggest](#autosuggest)
2.  [Geocoding](#geocode)   [`Legacy`]
3.  [Nearby](#nearby)
4.  [Reverse Geocode](#reverse-geocode)
5.  [Place detail](#place-details--eloc)
6.  [Distance](#driving-distance-matrix) [`Legacy`]
7.  [Routing](#routing) [`Legacy`]
8.  [Routing API](#routing-api)
9.  [Distance Matrix](#distance-matrix)
10. [Atlas Geocode](#atlas-geocode)

#### Autosuggest

##### Parameters

-  `client_id*`
-  `client_secret*`
-  `query*`
-  `successCallback*`
-  `errorCallback*`
- `location`
- `zoom`
- `region`
- `tokenizeAddress`
- `pod`
- `filter`

##### Syntax
```jsx
mmi_rest.atlas_auto(
{
client_id:  'clientId',
client_secret:  'clientSecret',
query:  'agr'
},SuccessCallback, Error  Callback);
```
##### Example

```js
mmi_rest.atlas_auto({client_id: 'clientId', client_secret: 'clientSecret',query: 'agr'},
function(result)
{
	console.log(result);
},
function(error)
{
	console.log(error);
});
```

#### Geocode
##### Parameters
-  `key*`
-  `addr*`
-  `successCallback*`
-  `errorCallback*`

##### Syntax

```js
mmi_rest.geocode(key: 'YOUR API KEY', addr: 'address'}, Success  Callback, Error  Callback);
```

##### Example

```js
mmi_rest.geocode({key:  'YOUR API KEY', addr:  'lucknow'},
function(result){
	console.log(JSON.stringify(result));
},
function(err){
	console.log(err);
});
```

#### Nearby
  
##### Parameters

-  `key*`
-  `client_id*`
-  `client_secret*`
-  `keywords*`
-  `refLocation*`
-  `successCallback*`
-  `errorCallback*`

##### Syntax

```js
mmi_rest.atlas_nearby({client_id:  'clientId', client_secret:  'clientSecret', keywords:  'beer', refLocation:  '28.631460,77.217423'}, SuccessCallback, ErrorCallback);
```

##### Example

```js
mmi_rest.atlas_nearby({client_id:  'clientId',client_secret:  'clientSecret',keywords:  'beer',refLocation:  '28.631460,77.217423'},
function(result)
{
	console.log(JSON.stringify(result));
},
function(error)
{
	console.log(error);
});
```

#### Reverse Geocode

##### Parameters

-  `key*`
-  `lat*`
-  `lng*`
-  `successCallback*`
-  `errorCallback*`
  
##### Syntax

```js
mmi_rest.rev_geocode(key: 'YOUR API KEY', lat: '27.61234', lng: '77.61234'}, Success  Callback, Error  Callback);
```

##### Example

```js
mmi_rest.rev_geocode({key:  'YOUR API KEY', lat:  '27.61234', lng:  '77.61234'},
function(result){
	console.log(JSON.stringify(result));
},
function(err){
	console.log(err);
});
```

#### Place Details / eLoc

##### Parameters

-  `key*`
-  `placeId*`
-  `successCallback*`
-  `errorCallback*`
  
##### Syntax
```js
mmi_rest.place_detail({key:  'YOUR API KEY', placeId:  'MMI000'}, Success  Callback, Error  Callback);
```
##### Example
```js
mmi_rest.place_detail({key:  'YOUR API KEY', placeId:  'MMI000'},
function(result)
{
	console.log(JSON.stringify(result));
},
function(err)
{
	console.log(err);
});
```

#### Driving Distance Matrix

##### Parameters


-  `key*`
-  `lat*`
-  `lng*`
-  `points*`
-  `successCallback*`
-  `errorCallback*`

##### Syntax

```js
mmi_rest.distance({key:  'YOUR API KEY', lat:  '27.61234', lng:  '77.61234', points:'29,78|30,78|28,79'}, Success  Callback, ErrorCallback);
```

##### Example

```js
mmi_rest.distance({key:  'YOUR API KEY', lat:  '27.61234', lng:  '77.61234', points:  '29,78|30,78|28,79'},
function(result)
{
	console.log(JSON.stringify(result));
},
function(err)
{
	console.log(err);
});
```

#### Routing (Deprecated)

##### Parameters

Note: "alternatives" and "advices" are optional parameters; send `null` if they are empty.

-  `key*`
-  `start*`
-  `destination*`
-  `successCallback*`
-  `errorCallback*`

##### Syntax
```js
mmi_rest.route({key:  'YOUR API KEY', start:  '28.111,77.111', destination:  '28.22,77.22', alternatives:  null, advices:  null}, SuccessCallback, ErrorCallback);
```
##### Example


```js
mmi_rest.route({key:  'YOUR API KEY', start:  '28.111,77.111', destination:  '28.22,77.22', alternatives:  null, advices:  null},
function(result)
{
	console.log(JSON.stringify(result));
},
function(err)
{
	console.log(JSON.stringify(err));
});
```

#### Routing API

##### Parameters

-  `key*`
-  `start*`
-  `destination*`
-  `successCallback*`
-  `errorCallback*`
-  `geometries`
-  `steps`
-  `exclude`
-  `rtype`
-  `region`
-  `bearings`
-  `alternatives`
-  `radiuses`
-  `overview`


##### Syntax

```js
mmi_rest.route_new({key:  'YOUR API KEY', start:  '77.131123,28.552413', destination:  '77.113091,28.544649'}, SuccessCallback, ErrorCallback);
```
##### Example

```js
mmi_rest.route_new({key:  'YOUR API KEY', start:  '77.131123,28.552413', destination:  '77.113091,28.544649'},
function(result)
{
	alert(JSON.stringify(result));
},
function(err)
{
	alert(JSON.stringify(err));
});
```

#### Atlas Geocode

##### Parameters
-  `client_id*`
-  `client_secret*`
-  `addr*`
-  `successCallback*`
-  `errorCallback*`
-  `itemCount`
-  `bias`
-  `podFilter`
-  `bound`
-  `scores`

##### Syntax

```js
mmi_rest.atlas_geocode({client_id:  'ID', client_secret:  'secret', addr:  'mapmyindia'}, Success  Callback, Error  Callback);
```

##### Example

```js
mmi_rest.atlas_geocode({client_id:  'ID', client_secret:  'secret', addr:  'mapmyindia'},
function(result)
{
	alert(JSON.stringify(result));
},
function(error)
{
	alert(error);
})
```

#### Distance Matrix

##### Parameters

-  `key*`
-  `source*`
-  `secondryLocations*`
-  `successCallback*`
-  `errorCallback*`
-  `rtype`
-  `region`
	
##### Syntax

```js
mmi_rest.distance_new({key:  'YOUR API KEY', source:  '77.983936,28.255904', secondryLocations:  '90.379249,23.497178'}, Success  Callback, ErrorCallback);
```
##### Example

```js
mmi_rest.distance_new({key:  'YOUR API KEY', source:  '77.983936,28.255904', secondryLocations:  '90.379249,23.497178'},
function(result)
{
	alert(JSON.stringify(result));
},
function(err)
{
	alert(err);
});
```

For any queries and support, please contact:

![Email](https://www.google.com/a/cpanel/mapmyindia.co.in/images/logo.gif?service=google_gsuite)
Email us at [apisupport@mapmyindia.com](mailto:apisupport@mapmyindia.com)

![](https://www.mapmyindia.com/api/img/icons/stack-overflow.png)

[Stack Overflow](https://stackoverflow.com/questions/tagged/mapmyindia-api)

Ask a question under the mapmyindia-api
![](https://www.mapmyindia.com/api/img/icons/support.png)
[Support](https://www.mapmyindia.com/api/index.php#f_cont)
Need support? contact us!

![](https://www.mapmyindia.com/api/img/icons/blog.png)
[Blog](http://www.mapmyindia.com/blog/)
Read about the latest updates & customer stories

  
  

> © Copyright 2019. CE Info Systems Pvt. Ltd. All Rights Reserved. | [Terms & Conditions](http://www.mapmyindia.com/api/terms-&-conditions)

> Written with [StackEdit](https://stackedit.io/) by MapmyIndia.