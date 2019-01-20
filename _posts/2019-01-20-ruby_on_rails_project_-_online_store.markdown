---
layout: post
title:      "Ruby on Rails Project - Online Store"
date:       2019-01-20 20:06:02 +0000
permalink:  ruby_on_rails_project_-_online_store
---


Hi everyone, 

The past few days, I've been working on using what I learned about Ruby on Rails and applying them all to create a project of my own. It's themed to be an online store; No specific type of store, but my goal was to create a web app to behave like an online store. This means that most of the features are there: creating an account, authenticating from a third party service, being able to "purchase" an item, and for an admin to modify any items listed on the site. Behind the scenes, we have CRUD controller actions, model validations, and database queries. 

Using Ruby on Rails is quite easy. Most of your file structure is generated, and all I had to do was create my models and migrations, and assign associations. When creating the controller actions, the biggest problem I faced was figuring out how to distinguish a log in from a third party service from a log in from a site-created account. But this was quite easily done by checking if we get nothing from requesting the authentication hash from Facebook. Everything else was easy because ActiveRecord ties everything together.
