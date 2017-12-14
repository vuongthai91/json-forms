# json-forms
[![bower version](https://img.shields.io/bower/v/json-forms.svg?style=flat-square)](#bower)
[![Build Status](https://api.travis-ci.org/brutusin/json-forms.svg?branch=master)](https://travis-ci.org/brutusin/json-forms)

`org.brutusin:json-forms` is a javascript library that generates HTML forms from [JSON Schemas](http://json-schema.org).

** Status **
I am not currently not having time to maintain this project, so first of all my apologies if some issues have been unresponded.
Branch v2 contains a completely new rearchitecture of the project, that I started several months ago but left unfinished. If someone is interested in continuing my work I will be happy to guide them

**Table of Contents:** 

- [org.brutusin:json-forms](#)
  - [Features](#features)
  - [Usage](#usage)
  - [Demo](#demo)
  - [Dynamic schemas](#dynamic-schemas)
  - [API](#api)
  - [CDN](#cdn)
  - [Support, bugs and requests](#support-bugs-and-requests)
  - [Authors](#authors)
  - [License](#license)

## Features
* Dynamic schemas support
* Extensible and customizable
* No external libraries needed
* Validation
* Multiple forms per document supported

## Usage
Include the main library dependencies:
```html
<link rel="stylesheet" href='dist/css/brutusin-json-forms.min.css'/>
<script src="dist/js/brutusin-json-forms.min.js"></script>
```
Optionally, include the bootstrap extension (requires bootstrap):
```html
<script src="dist/js/brutusin-json-forms-bootstrap.min.js"></script>
```
Create the javascript `BrutusinForms` instance, `schema` being a javascript `object` representing the schema structure:
```javascript
var schema = {"type": "boolean"}
var BrutusinForms = brutusin["json-forms"];
var bf = BrutusinForms.create(schema);
```
And finally render the form inside a container with optional preloaded JSON initial data, `data`:
```javascript
var container = document.getElementById('container');
bf.render(container, data);
```

## Demo
[![demo](http://brutusin.org/json-forms/img/json-forms.png)](http://brutusin.org/json-forms/)
http://brutusin.org/json-forms/

## Dynamic schemas
This library supports dynamic schemas, that is, subschemas that can change depending on the value of other parts of the data.

This lets creating **dynamic forms** that vary their shape depending on the values entered by the user. This is extremely useful for big autogenerated schemas, that aggregates lots of subschemas and have functional bindings, given that it allows to show the user a simpler, non-error-prone form, also avoiding asking for unneeded data.

Dynamic schemas are built upon two main blocks: 
* Custom (non-standard) schema property called `dependsOn`, to build the subschemas dependency graph 
* [Brutusin DSL for path expressions](https://github.com/brutusin/json#path-expressions), for identifying subschemas.

### `dependsOn` schema extension
### Dynamic schema resolution

## API
### Static members:

Member|Description
------| -------
`BrutusinForms.create(schema)`|BrutusinForms factory method
`BrutusinForms.addDecorator(f(htmlElement, schema))`| Register a callback function to be notified after an HTML element has been rendered (passed as parameter). See [brutusin-json-forms-bootstrap.js](src/js/brutusin-json-forms-bootstrap.js) for an example of *bootstrap* decorator.
`BrutusinForms.postRender(instance)`|Callback function to be notified after a BrutusinForms instance has been rendered (passed as parameter)
`BrutusinForms.instances`|Array containing all the BrutusinForms instances created in the document by the factory method.

### Instance members:

Member|Description
------| -------
`bf.render(container, data)`| Renders the form inside the the container, with the specified data preloaded
`bf.validate()`| Returns `true` if the input data entered by the user passes validation
`bf.getData()`| Returns the javascript object with the data entered by the user
`bf.schemaResolver(schemaIdArray, data)`| Schema resolver for [dynamic schemas](#dynamic-schemas)

## CDN

http://www.jsdelivr.com/projects/brutusin.json-forms

## Support bugs and requests
https://github.com/brutusin/json-forms/issues

## Authors

- Ignacio del Valle Alles (<https://github.com/idelvall/>)

Contributions are always welcome and greatly appreciated!

## License
Apache License, Version 2.0
