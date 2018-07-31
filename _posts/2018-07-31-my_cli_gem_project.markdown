---
layout: post
title:      "My CLI Gem Project"
date:       2018-07-31 20:21:08 +0000
permalink:  my_cli_gem_project
---

Hey guys!

I recently worked on creating a CLI gem. The general idea was to create a command line interface that scrapes data from a website, creates an object using that information, and displays it in front of the user to interact with. As a personal food lover, I wanted to create a program that incorporates food. In my third year of college, I'll be living in an apartment with no meal plan, and I have no idea how to cook. So this gem could help anyone in need of new recipes to learn. In this blog, I'll be describing my thinking process as I was creating the gem. 

First, I thought about what I wanted my project to look like on the command line. This involved writing code that is hard-coded so that I can visualize what I want it to look like, and it helps you figure out what methods or classes are needed in your program. This is how I imagined it to look like: first the user is welcomed on the command line interface and it describes to you how each list is formatted, and how to use the program. So you'll be prompted to enter which list you want to view first, (1-5)(6-10)(11-15)(16-20)(21-25). Each list contains 5 recipe names with a number corresponding to each recipe. If one of the recipes interests you, you can type in the number and it will provide you with a details page, which tells you everything about the recipe, like servings, time, rating, ingredients, and directions. If you want to view another list, you can enter the list range and select a recipe from there, or if you're done you can type 'exit' to quit. 

Moving on, since my data was currently hard-coded, I needed to be able to grab that information in a more efficient way. This can be achieved by creating a class called Recipe. An instance of the Recipe class will be responsible for holding all the attributes of a recipe. `attr_accessor :name, :url, :total_time, :yield, :author, :rating, :ingredients, :directions` The `self.create` method is a class method that takes in an array of hashes (each hash representing the attributes of one recipe) and creates a new instance and saves it in the class variable `@@all[]` 

The next part is learning how to incorporate a scraper class to generalize scraping data from an outside source. The scraper class has a generalized method #get_page which utilizes open-uri to grab the html from a website, and nokogiri puts the html into nested node form. After grabbing the HTML, you play around with the pry debugger to try to grab the element you want from the website. #scrape_list_page scrapes the name and url from the index page and returns an array of hashes that include the name and url key-value pairs. These are used to instantiate a Recipe object. #scrape_recipe_page scrapes all the other values mentioned above, and returns a hash of these attributes, which will be used to add onto an existing instance. If you look in recipe.rb, I used the send method to generalize setting an instance's attributes. While, #initalize and #add_attributes look the same, the latter is necessary in order to not add a duplicate instance in the class collection.

Last of all, having the recipe class and scraper class defined, I had to go back to the CLI to incorporate the two. The hardest part was cutting down the code by generalizing it. For example, it's easier to iterate printing out an item, rather than using `puts` multiple times. I understood that other people could be reviewing my code, and the same program with the least amount of code is better. So generalizing was very important to me. Then, I went back to add basic comments so people who read my code could have a better understanding of what a portion of my code did.

That's it! Overall, it was a good experience to utilize what I learned previously before about object orientation, and apply it. Stay tuned for more in the future!
