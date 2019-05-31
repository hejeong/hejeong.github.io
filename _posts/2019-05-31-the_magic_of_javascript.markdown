---
layout: post
title:      "The Magic of Javascript"
date:       2019-05-31 13:33:40 -0400
permalink:  the_magic_of_javascript
---

My most recent project involved adding Javascript to my Rails application. Javascript deals with a lot of the animations you see on web pages, but it also allows you to modify what the viewer sees without them knowing about what's actually going on. That's the magic of Javascript; the art of deceptive tricks. You might think that clicking on a link on the page redirects you to another page, but javascript is really just swapping out the elements on the page with the desired result.

I utilized Active Model Serializers to create JSON objects for any models I had, so that I could dynamically render objects with the proper information. For example, the route '/items' used to redirect to the index page, but now I can render the same thing without redirecting to a different URL. This is possible by binding event listeners to buttons on the page. One mistake I made was using jquery to attach event listeners directly to an element. So, whenever you redirect to a page, the button is no longer bounded. I learned that you should attach the event listener to the document, then assign it to the class you wish to perform the action. That way, no matter what elements are removed or added to the DOM, the elements that have that class or id tag will get the bind. You can also submit forms dynamically, using AJAX post requests. 

This is how my web app looks right now.
![hey](https://imgur.com/a/CTgi47H)

You can check it out for yourself [here.](https://github.com/hejeong/ruby-on-rails-portfolio-project)
