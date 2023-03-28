# ![tarant-react](https://user-images.githubusercontent.com/3071208/228214632-97499cb2-d6c4-4562-9e64-cdbd6a9dfc1b.png)


![Downloads](https://img.shields.io/npm/dt/tarant-react.svg)
[![npm](https://img.shields.io/npm/v/tarant-react.svg)](https://www.npmjs.com/package/tarant-react)
![npm](https://img.shields.io/npm/l/tarant-react.svg)
![GitHub Workflow Status](https://img.shields.io/github/actions/workflow/status/tarantx/tarant-react/build.yml?branch=main)
[![All Contributors](https://img.shields.io/badge/all_contributors-0-orange.svg?style=flat-square)](#contributors-)
[![Maintainability](https://api.codeclimate.com/v1/badges/d0264ba3d46b064b1293/maintainability)](https://codeclimate.com/github/tarantx/tarant-react/maintainability)
[![Test Coverage](https://api.codeclimate.com/v1/badges/d0264ba3d46b064b1293/test_coverage)](https://codeclimate.com/github/tarantx/tarant-react/test_coverage)
![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)
![issues Welcome](https://img.shields.io/badge/issues-welcome-brightgreen.svg)
![GitHub issues](https://img.shields.io/github/issues/tarantx/tarant-react.svg)
![GitHub pull requests](https://img.shields.io/github/issues-pr/tarantx/tarant-react.svg)

## Motivation

Provide the capabilities to actors to be render using the react framework.

## Installation

add it to your project using `npm install tarant-react --save` or `yarn add tarant-react`

## Usage

Extend the react actor with a template and the properties to bind to the id of the actor will relate to the html component id

```js
import React from "react";
import { decorator } from "../../utils/decorator"
import { AppActor } from "../AppActor"

export class ReactDecorator extends decorator<AppActor> {
    constructor(actor: AppActor) {
        super(actor)
    }

    render() {
        return (<div id="app"><button onClick={(this.actor as any).self.addOne}>{this.actor.counter}</button></div>)
    }

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

