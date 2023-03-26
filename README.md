# Tarant React


[![npm](https://img.shields.io/npm/v/tarant-react.svg)](https://www.npmjs.com/package/tarant-react)
[![Build Status](https://travis-ci.org/tarantx/tarant-react.svg?branch=master)](https://travis-ci.org/tarantx/tarant-react)
[![Coverage Status](https://coveralls.io/repos/github/tarantx/tarant-react/badge.svg?branch=master)](https://coveralls.io/github/tarantx/tarant-react?branch=master)
![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)
![issues Welcome](https://img.shields.io/badge/issues-welcome-brightgreen.svg)
![npm](https://img.shields.io/npm/l/tarant-react.svg)
![GitHub issues](https://img.shields.io/github/issues/tarantx/tarant-react.svg)
![GitHub pull requests](https://img.shields.io/github/issues-pr/tarantx/tarant-react.svg)
![Downloads](https://img.shields.io/npm/dt/tarant-react.svg)

## Motivation

Provide the capabilities to actors to be render using the react framework.

## Installation

add it to your project using `npm install tarant-react --save` or `yarn add tarant-react`

## Usage

Extend the react actor with a template and the properties to bind to the id of the actor will relate to the html component id

```js
import { ReactActor } from "tarant-react";

export default class AppActor extends ReactActor {
    constructor() {
      super("#app")
      this.schedule(1000, this.incrementCounter, [])
    }
  
    private incrementCounter(): void {
      this.counter++;
    }

    private counter = 0; 
    readonly template : string = "<div>counter: {{counter}}</div>"
}
```

Initialize the actor system with the provided materializer
```js
import { ActorSystem, ActorSystemConfigurationBuilder } from 'tarant'
import AppActor from './Actor/AppActor';
import { ReactRenderer } from 'tarant-react';

window.onload = () => {
  const system = ActorSystem.for(ActorSystemConfigurationBuilder.define()
  .withMaterializer(new reactRenderer())
  .done())  
  system.actorOf(AppActor)
}
```
##### Created my free [logo](https://logomakr.com/3zsWGM) at <a href="http://logomakr.com" title="Logo Makr">LogoMakr.com</a> 