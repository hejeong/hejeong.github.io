---
layout: post
title:      "Sinatra: Resell Your College Textbooks"
date:       2018-08-24 16:01:45 -0400
permalink:  sinatra_resell_your_college_textbooks
---


Hey everyone! Let me introduce you to my website application I created using the Sinatra framework with ActiveRecord. It is a platform for registered users to sell or buy used college textbooks!

I was inspired by my current experience in college. College is already so expensive, yet we still have to pay hundreds for textbooks. And if you want to resell them to the campus bookstore, you'll be lucky to get even 25% of the value back. That's why a lot of students like to resell to other students instead, to help everyone else out. There isn't really a good place to do that though. Most people use facebook groups to post them, but personally I find it too messy. So I created Sinatra College Textbooks!

I used a ruby gem called Corneal (which is learn co scrambled) created by another Learn Verified student. Huge credits to the creator; I would check his awesome gem out! (https://github.com/thebrianemory/corneal) This gem helped create the basic file structure of a Sinatra application. It has many more functionalities, but I only used it to create the basic file tree, which follows the MVC (Model View Controller) structure. 

It was actually pretty easy to get started. I began with the migrations and models, which is simple in my case because I only have users and textbook models. After that, everything come easily. The MVC structure enables you to focus on one thing at a time (separation of concerns) so I began with the login and sign up pages. First I wrote the users controller, and then built the necessary routes and view pages. Some routes would then redirect to the textbooks index page, and then I began writing in the textbooks controller to implement the CRUD actions (Create, Read, Update, and Destroy). Of course, you need to worry about validations, but I like to see what I have first, then build on top. So I built my minimum viable product, just having the basic operations, like filling out a form, creating or editing the object and save it to the database, and basic navigation tools. Validations were the trickiest part. The easy ones were checking to see if the input fields were blank, and if they were, don't allow them to. Then you have to check that only logged in users can view content. I found my self reusing a lot of code, so in my helper methods, I did all the logic and redirection in the method declarations. This was my solution:
```
def logged_in?
   if session[:user_id] == nil
      flash[:message] = "Please login first."
      redirect to '/login'
   end
   true
end
```
 
Now, I could just insert one line of code to every place that requires this type of validation. Developer-friendly :)
Then you had to check that only owners can edit or delete and textbook. This wasn't hard either, I hid the edit/delete buttons from the view page if you aren't the owner. The tricky parts are finding the "loopholes". I found that if you entered the url for the edit page, i.e. ```/textbooks/3/edit``` Then you can still get to the edit form. Obviously, we don't want this "feature" so the simple fix was checking the current user and see if it matches the textbook's owner. If not, you redirect to another page and use a flash message to warn them that you can't edit someone else's listing.

The rest was just some CSS styling, which I'm not very good at, and thankfully the Corneal gem provided some basic styling, so I played around with a couple things, like buttons, form styles, etc. It's my first attempt, but I think it looks decent!

By the time I finished the requirements, I thought about adding a submit feature. It would complicate things a little bit, but I'm glad I got it done! Users will now see a purchase button (unless you own it) which you can "purchase" the item, and the listing gets removed from the index page. However, the information is still saved on a user's profile page. (User's profile page lists all of a user's current listings, and purchase history).

It took me about a day and a half to finish, and it's amazing to realize how much I have learned so far. I had lots of fun making this, and I can actually see myself building on top of this to implement it in the future!
Feel free to check my project out! 

Github Repo: [Sinatra College Textbooks](https://github.com/hejeong/college-textbooks-sinatra-project)

The final (for now) product looks like this: 

*Log In Page:*

<img src="https://i.imgur.com/oB0mHFj.png" width="100%">

*Index Page*

<img src="https://i.imgur.com/NiAhG1O.png" width="100%">

*Item Show Page*

<img src="https://i.imgur.com/boprOIX.png" width="100%">
