---
lang: en
title: 'Getting started'
keywords: LoopBack 4.0, LoopBack 4
tags:
sidebar: lb4_sidebar
permalink: /doc/en/lb4/Getting-started.html
summary:
---
## Prerequisites: JavaScript

Like other modern JavaScript frameworks (for example, Angular 2 and React) LoopBack 4 has an opinion about what flavor of JavaScript to use in your application.
The starting point is [ECMAScript 6](http://www.ecma-international.org/ecma-262/6.0/), plus the following non-standard add-ons:

 - Decorators
 - `async` / `await`
 - ES2015-modules

**All examples and snippets in the documentation use this flavor of JavaScript.**

{% include note.html content="This article will eventually cover:
- How to install the command line utility
- Using the utility to scaffold the skeleton app
- Running the app (node ., npm start)
" %}

## A simple example

Here is the most basic LoopBack 4 application:

```ts
import {Application} from '@loopback/core';
import {RestComponent, RestServer} from '@loopback/rest';

const app = new Application({
  components: [RestComponent],
});

(async function start() {
  // Grab the REST server instance
  const server = await app.getServer(RestServer);
  // Setup our handler!
  server.handler((sequence, request, response) => {
    sequence.send(response, 'hello world');
  });
  await app.start();
  console.log(`REST server listening on port ${server.getSync('rest.port')}`);
})();
```

The example above creates an `Application` and a `RestServer` that responds to all HTTP requests with the text "Hello World".

To see what the complete application looks like, see [loopback-next-hello-world](https://github.com/strongloop/loopback-next-hello-world/).

The following guides introduce the fundamental concepts of LoopBack 4 required to build scalable, maintainable, and consistent APIs.

If you want to try it out locally follow the instructions in [Installation](Installation.html).  
