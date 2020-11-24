![](header.png)

[![NPM Version][npm-image]][npm-url]
[![Build Status][travis-image]][travis-url]
[![Downloads Stats][npm-downloads]][npm-url]

# Slick Svero
> Slick Svero is the router for svelte.

## Installation

```sh
npm install slick-svero --save
```

## Usage example

Below is a short example on how to use the router.

```js
<!-- App.svelte -->
<script>
import { Router, Route } from "slick-svero";
import Home from "./components/Home.svelte";
import About from "./components/About.svelte";
import Article from "./components/Article.svelte";
</script>

<Router>		
  <Route path="/" component="{Home}" />
  <Route path="/about">
    <h1>Welcome to about!</h1>
  </Route>
  <Route path="/article/:url" component="{Article}"  let:params />  	
</Router>
```


```js
// server.js
var express = require('express');

var app = express();

app.use(express.static('public'));

app.get('*', (req, res) => {
  res.sendFile(__dirname + "/public/index.html")
})

app.listen(3000, () => {
  console.log("App listening on port 3000")
});
```

_For more usage examples, see the [Wiki][wiki] or access the examples folder._


# API

## Router
This component provides context-based routing for the Link and Route component and should be used to encapsulate these components. There is only one property which is optional.


## Route
This component is used to render a component or markup if its path matches the URL. An object called path is needed, which is the path that, when matched, the route will be rendered.

### Properties


| Prop      | Required | Default     | Description                                                                |
| --------- |:--------:|:-----------:| -------------------------------------------------------------------------- |
| path      | yes      | `"/"`       | The path relative to the origin that the `Route`                           |
|           |          |             |                                                                            | 
| component | no       | `undefined` | The component to be rendered.                                              |
|           |          |             |                                                                            |
| params    | no       |   `" "`     | The params for use in componet                                             | 



## Release History

* 1.0.0
    * Work in progress

## Meta

Antoniel Bordin – antonielbordin@hotmail.com

Distributed under the MIT license. See ``LICENSE`` for more information.

[https://github.com/antonielbordin/slick-svero](https://github.com/dbader/)

## Contributing

1. Fork it (<https://github.com/antonielbordin/slick-svero/fork>)
2. Create your feature branch (`git checkout -b feature/fooBar`)
3. Commit your changes (`git commit -am 'Add some fooBar'`)
4. Push to the branch (`git push origin feature/fooBar`)
5. Create a new Pull Request

<!-- Markdown link & img dfn's -->
[npm-image]: https://img.shields.io/npm/v/datadog-metrics.svg?style=flat-square
[npm-url]: https://npmjs.org/package/datadog-metrics
[npm-downloads]: https://img.shields.io/npm/dm/datadog-metrics.svg?style=flat-square
[travis-image]: https://img.shields.io/travis/dbader/node-datadog-metrics/master.svg?style=flat-square
[travis-url]: https://travis-ci.org/dbader/node-datadog-metrics
[wiki]: https://github.com/antonielbordin/slick-svero/wiki

