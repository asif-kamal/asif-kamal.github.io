---
layout: post
title:      "The fun and the trouble with coding."
date:       2020-04-10 10:39:55 -0400
permalink:  the_fun_and_the_trouble_with_coding
---


So far in my Sinatra Portfolio Project, I've relearned what I knew from taking UX Design courses, and utilized those skills and came up with what I have now :)

Revisiting CSS and HTML and incorporating it into Ruby has been interesting. 

The trouble I had in the last couple nights of working on my project was how small an error could cause my program to fail. A couple examples:

When first running shotgun I ran into errors for migrating tables. I was supposed to have done that before my website could load. I wrote my code off of old files from other lessons and so I had mixed up code for awhile inside my repo. I had to search online to see how to remove old seed.rb files and undo sql databases. 

Basically, alot of rereading old lesson and trying things out in my atom environment. Tweak this and that. Some of my fear in software engineering came from how minute changes could cause programs to fail. 

I started off following my cohort leads advice when creating a new app but after serching through different ways to building a Sinatra website application I found other ways to wrting code that worked better in my case. 

I think the hardest part for me was combining sql, erb tags and ruby, and trying to keep all the new concepts in my memory. The fun part was when after fixing my migrations tables I could see what I had through shotgun what my website actually looked like. I'm very unfamiliar with the environment file, so I avoided touching anything in there. And CSS styling can be very time consuming and I consider it more of an art than pure fullstack development. 

I also ran into the problem of making sure my views files displayed the right information based on my models. One example was trying to get my project.title to display but failing.

```
@project.title
```
was for some reason not working in my project index.erb file. I was using the find_by_title method instead of the find_by_id method I am using now to look up projects in my projects controller. Not too clear why it's working now, but hopefully I can find out why soon.



**EDIT:**

ActiveRecord Validations

They are used to *validate* data being saved to the database. If for example for an email params a user incorrectly types in an email address, the entry will not be kept. The methods     .create    .save     and   .update    all use validations automatically to ensure the data being saved is valid. If I use !(bang) on the  .create    .save   and    .update methods I will receive an exception for invaild data. 

ActiveRecord validations help me keep an active record of data in my database. Which is the point.




