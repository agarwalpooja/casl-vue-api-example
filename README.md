# CASL integration example with Vue + Vuex + REST API

This example shows how to integrate [CASL](https://github.com/stalniy/casl) auhorization in more or less real [Vue](https://vuejs.org) application with Vuex and REST API. Read [CASL and Cancan](https://medium.com/dailyjs/casl-and-cancan-permissions-sharing-between-ui-and-api-5f1fa8b4bec) for details 

> Generate with vue-cli

## Installation

``` bash
# install vue cli 3
npm install -g @vue/cli

# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run serve
```

## Description

This application is a basic Blog application with possibility to login, logout and manage articles. User abilities are received from REST API and later stored in localStorage.

`Ability` plugin for Vuex store can be found in [src/store/ability.js](src/store/ability.js).
When user successfully login (i.e., `createSession` mutation is dispatched in store), ability is updated and when user logout (i.e., `destroySession` mutation is dispatched) ability is reset to read-only mode.

`http` service is built on top of Fetch API with some hacky code (it is not important for this example).
Also this example uses [vuetify](https://vuetifyjs.com/en/) as UI library

## Server side

REST API is expected to be available at `http://localhost:3000/api` and support CORS headers.
This example was tested and implemented together with [Rails5 + Cancan](https://github.com/stalniy/rails-cancan-api-example) but API can be implemented in whatever language you want.
It's just a showcase that CASL can be seamlessly integrated with awesome [Cancan](https://github.com/CanCanCommunity/cancancan) ruby gem

If you setup rails application, there are 2 users available:
* admin - admin@freaksidea.com / 123456
* member - member@freaksidea.com / 123456
