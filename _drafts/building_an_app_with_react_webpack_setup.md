---
layout: post
title: Building an App with React and Webpack Rails Api
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

NginX
-----

There's two ways we can handle the API for our app. We can keep it on the same domain, but on a different port. Or we can put it on a subdomain, enabling easy scaling in the future. In this tutorial, we'll be running the API as a subdomain.

No matter which route we take, however, we must decide how we'll be retrieving the data from our API via ajax requests.

#### Option 1: CORS requests
The same-origin policy prevents us from making ajax requests from one location to another (even if the target resource is on the same domain). We'd need to enable the Cross-Origin Resource Sharing (CORS) mechanism in order for us to get this working. I won't go down this path, and if you decide to, make sure you're aware of the security pitfalls. CSRF security holes exploit CORS vulnerabilities.

#### Option 2: Proxy ajax requests via NginX
Instead, we can let NginX handle proxying of requests. 

Install NginX:

    brew install nginx

Edit nginx.conf

    sudo nano /usr/local/etc/nginx/nginx.conf

We'll need to add two upstreams and some location configurations so the NginX server knows where to route requests. The nginx.config file I use is below

    #TODO

You should be all set to run nginx. Do so by running:

    sudo nginx




Node/NPM
--------

We'll be using ES2015 features, so we'll need the latest and greatest Node.

NPM init
--------

Feel free to create your package.json yourself, but I prefer the prompts provided by NPM init. Nice and easy.

Postgresql
----------

I prefer to use Postgresql, but you can pretty easily switch that out for MySql or another db. I've seen a lot of tutorials using MongoDB, but I have no experience with it whatsoever.
