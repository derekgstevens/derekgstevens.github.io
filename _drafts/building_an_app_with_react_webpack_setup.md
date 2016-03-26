---
layout: post
title: Building an App with React and Webpack
---

Intro
-----

Welcome to Building an App with React and Webpack, a deceiving title to say the least. This series will cover far more than just React and Webpack, taking you on a whirlwind tour of the React ecosystem and a 'Choose Your Own Adventure' style API/backend section (that will be explained in just a bit). To be perfectly honest, I don't know React and have very little experience with the other technologies that will appear in the series. This is as much a learning experience for me as I hope it will be for you!

###Choose Your Own Adventure?
We'll start with getting some of the underlying setup out of the way, before moving on to a bit of frontend work with React. After that, though, things might get a little hard to follow: I'll be creating multiple APIs in different languages to act as the backend to our React code. Each API will implement the same endpoints and integrate with Postgresql, but again, I'm using this series to learn and will be exploring some new languages myself. The image below shows the different paths to choose from, and I'll update its progress as new posts are published.

Ready to get started? Let's get installing!


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

Postgresql/PgAdmin
-----------------

I prefer to use Postgresql, but you can pretty easily switch that out for MySql or another db. I've seen a lot of tutorials using MongoDB, but I have no experience with it whatsoever.

Git
---
