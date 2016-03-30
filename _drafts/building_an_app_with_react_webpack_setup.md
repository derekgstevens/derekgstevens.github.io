---
layout: post
title: Building an App with React and Webpack
---

Intro
-----

Welcome to Building an App with React and Webpack, a deceiving title to say the least. This series will cover far more than just React and Webpack, taking you on a whirlwind tour of the React ecosystem and a 'Choose Your Own Adventure' style API/backend section (that will be explained in just a bit). To be perfectly honest, I don't know React and have very little experience with the other technologies that will appear in the series. This is as much a learning experience for me as I hope it will be for you!

###Choose Your Own Adventure?
We'll start by getting some of the underlying setup out of the way, before moving on to a bit of frontend work with React. After that, though, things might get a little hard to follow: I'll be creating multiple APIs in different languages/frameworks to act as the backend to our React code. Each API will implement the same endpoints and integrate with Postgresql, but again, I'm using this series to learn and will be exploring some new languages myself. The image below shows the different paths to choose from, and I'll update its progress as new posts are published.

Ready to get started? Let's get installing!


NginX
-----

Since our api won't be running from within our app, there's two ways we can handle calls to our API. We can keep it on the same domain, but on a different port. Or we can put it on a subdomain. In this tutorial, we'll be running the API as a subdomain.

No matter which route we take, however, we must decide how we'll be retrieving the data from our API via ajax requests. The same-origin policy prevents us from making ajax requests from one location to another (even if the target resource is on the same domain).

#### Option 1: CORS requests
 We'd need to enable the Cross-Origin Resource Sharing (CORS) mechanism in order for us to get this working. While there are plenty of helpful libraries out there to accomplish this, I'd rather not deal with it.

#### Option 2: Reverse proxy ajax requests via NginX
Instead, we can let the free http server NginX handle proxying of requests.

Installing NginX is easy on a Mac or Linux. Here's how it's done:

Mac
    brew install nginx
Ubuntu
    sudo apt-get install nginx


Node/NPM
--------

We'll be using ES2015 features, so we'll need the latest and greatest Node. At the time of writing, that's version 5.9.1. We'll be using NVM (node version manager) to install and manage Node.

Mac
  curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.31.0/install.sh | bash

Ubuntu
  wget -qO- https://raw.githubusercontent.com/creationix/nvm/v0.31.0/install.sh | bash

After installing nvm, let's actually install nodejs and tell nvm to use that version as the default.

  nvm install 5.9.1
  nvm use 5.9.1
  nvm alias default 5.9.1

The above nodejs installation should take care of installing npm as well (nifty!). Do a quick sanity check by running npm -v. It should return at least v3.8.3. If not, you can easily update by running:

  npm install -g npm

Postgresql/PgAdmin
-----------------

I prefer to use Postgresql, but you can pretty easily switch that out for MySql or another db. I've seen a lot of tutorials using MongoDB, but I have no experience with it whatsoever. We'll also install PgAdmin, so we get a nice UI when interacting with our database. We'll be using v9.4 of Postgresql, which should be easy to install. If you're running an older version of Ubuntu however, please refer to the [official documentation](http://www.postgresql.org/download/linux/ubuntu/)

Ubuntu
  sudo apt-get install postgresql-9.4

Installing pgAdmin is another one-liner

Ubuntu
  sudo apt-get install pgadmin3

Git
---
