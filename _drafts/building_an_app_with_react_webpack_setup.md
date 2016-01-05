---
layout: post
title: Building an App with React and Webpack: Rails Api
categories: backend, Rails
---

* Git
  * Api & App separate repos
* NginX
* Node/NPM
* NPM init
* Postgresql


Git
---

We'll be creating two different git repos for this app: one for the api and one for the app itself. Yes, it's possible to have both in the same repo, but I prefer two separate repos for scaling reasons.

#TODO -- reasons for separate api/app repos

This does add some extra complications, but I believe the benefits outweigh the detriments. You can find the repo for the frontend portion of this tutorial [here](https://github.com/derekgstevens/react-boilerplate). Again, there's two flavors for the api: [Koa.js](https://github.com/derekgstevens/koa-api-boilerplate) and [Rails](https://github.com/derekgstevens/rails-api-boilerplate). Go ahead and clone the frontend and your choice of API to your development machine.

    git clone https://github.com/derekgstevens/react-boilerplate.git
    git clone https://github.com/derekgstevens/koa-api-boilerplate.git
    git clone https://github.com/derekgstevens/rails-api-boilerplate.git

Once cloned, let's quickly update the .gitignore files.

##### For Rails
    .DS_Store

##### For Koa.js
    node_modules/
    npm-debug.log
    .DS_Store

##### For React Frontend App
    node_modules/
    build/
    npm-debug.log
    .DS_Store

Don't worry about the overarching project directory structure just yet, we'll cover that in future parts of this tutorial. 
