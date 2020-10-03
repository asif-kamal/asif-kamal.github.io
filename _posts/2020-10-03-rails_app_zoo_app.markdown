---
layout: post
title:      "Rails App: Zoo App"
date:       2020-10-03 12:18:01 +0000
permalink:  rails_app_zoo_app
---


I have created a Rails web application called Zoo App. Its primary function is to let zookeepers have a convenient way to record their observations on the health and welfare of the animals kept under care.

I started by creating a new Rails app through the terminal.

```
rails new ZooApp
```

Probably the toughest part about my app was building the ReportsController. Since the report model serves as a join table between User and Animal I had to find a way to create a new report using both foreign keys.

![ReportsController](https://i.ibb.co/fpVDKw5/Screen-Shot-2020-10-03-at-7-58-19-AM.png)

I was not sure at first whether to have the nested new route coming from the user side or the animal side. 

```
 animal_reports GET    /animals/:animal_id/reports(.:format)                                                    reports#index
                                      POST   /animals/:animal_id/reports(.:format)                                                    reports#create
                    new_animal_report GET    /animals/:animal_id/reports/new(.:format)                                                reports#new
                   edit_animal_report GET    /animals/:animal_id/reports/:id/edit(.:format)                                           reports#edit
                        animal_report GET    /animals/:animal_id/reports/:id(.:format)                                                reports#show
                                      PATCH  /animals/:animal_id/reports/:id(.:format)                                                reports#update
                                      PUT    /animals/:animal_id/reports/:id(.:format)                                                reports#update
                                      DELETE /animals/:animal_id/reports/:id(.:format)                                                reports#destroy
                              animals GET    /animals(.:format)                                                                       animals#index
                                      POST   /animals(.:format)                                                                       animals#create
                           new_animal GET    /animals/new(.:format)                                                                   animals#new
                          edit_animal GET    /animals/:id/edit(.:format)                                                              animals#edit
                               animal GET    /animals/:id(.:format)                                                                   animals#show
                                      PATCH  /animals/:id(.:format)                                                                   animals#update
                                      PUT    /animals/:id(.:format)                                                                   animals#update
                                      DELETE /animals/:id(.:format)                                                                   animals#destroy
                         user_reports GET    /users/:user_id/reports(.:format)                                                        reports#index
                                      POST   /users/:user_id/reports(.:format)                                                        reports#create
                      new_user_report GET    /users/:user_id/reports/new(.:format)                                                    reports#new
                     edit_user_report GET    /users/:user_id/reports/:id/edit(.:format)                                               reports#edit
                          user_report GET    /users/:user_id/reports/:id(.:format)                                               
```

I decided to route all new report instances through the user parent resource, and to have the reports index view display only the specific animal.  

Here I used `new_user_report_path`.
![Using new_user_report_path](https://i.ibb.co/CP2rGxr/Screen-Shot-2020-10-03-at-8-06-15-AM.png)

Here I used `animal_reports_path`.
![Using animal_reports_path](https://i.ibb.co/R43WCc7/Screen-Shot-2020-10-03-at-8-06-39-AM.png)

Not worrying too much on looks I worked mainly on getting the create action working in harmony with my views. 
I would say this project was not too difficult when you know what to prioritize versus not knowing. I enjoyed working through the Rails module and I would say I definitely have a greater grasp on how things work :)

