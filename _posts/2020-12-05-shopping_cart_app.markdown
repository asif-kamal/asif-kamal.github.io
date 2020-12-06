---
layout: post
title:      "Shopping Cart App"
date:       2020-12-06 03:44:07 +0000
permalink:  shopping_cart_app
---


I have been working on the Javascript Frontend/Rails API backend project and have come to a satisfactory close. 
![Screenshot of Web App in Browser](https://i.ibb.co/jrfmnRQ/Screen-Shot-2020-12-05-at-9-48-44-PM.png)

This project took me some time to figure out. Namely the most difficult part was to comprehend the new concepts in this module. Using functions to create a working Javascript frontend was interesting. From the onset, when I came up with the idea to build a shopping cart app many factors came into play. 

I started by running `rails new javascript-shopping-cart-backend --api --database=postgresql`. Once the api was created I decided to use items and categories as migration tables. Since this was a Single-page application having a has many relationship for categories to items made sense. 

Creating the CRUD actions needed for fetching item data took me no time. An index action for Items Controller to display all the json data brought my attention to how I should have items rendered if the user selected a category.

![Migration files](https://ibb.co/zVV04z3)
![Dropdown](https://ibb.co/xMNpPTX)

The dropdown selection worked through an AJAX call through the category id of the items. The option value of the category selected in HTML is used in the url of the fetch request as the id for a nested route: `${CATEGORIES_URL}/${id}/items` . 

![Seed Data](https://ibb.co/zVV04z3)

I had used seed data with items assigned category ids to make simpler rendering the specific items on the DOM. 

Styling had been an issue with my project which I dealt with by implementing Bootstrap. I did not want to spend too much time learning css and html, but needed to work with a layout in order to continue creating functions on the buttons of the Shopping Cart App.

For each item in the json data I created a `renderItemCard` function which appended each div card to the `<main>`  tage in the html.

After successfully having the items rendered, I moved the quantity plus/minus buttons to a table where the total is calculated. This made more sense. I kept the add to cart button in the div card of each item so the user can decide the quantity after it has been added to the cart. 
![Quantity plus and minus buttons](https://ibb.co/cxf6rh8)

I had originally worked on creating purely constructor functions. Later, after getting my app to fully function I switched over to using classes. I divided up my index.js file into three files called: ApiService.js, Item.js and ItemForm.js. 
Most of the functions I created are in index.js which apply to manipulating items once they have been added to the cart.

One interesting concept I learned was modular Javascript. The ApiService helped clean up my code by only handling the fetch requests. I had difficulty parsing through my code until breaking it up and using classes. 

All in all I enjoyed creating a Frontend JS/Rails backend project. 
