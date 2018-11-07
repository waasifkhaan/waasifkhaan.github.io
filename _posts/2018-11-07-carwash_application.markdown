---
layout: post
title:      "CarWash Application"
date:       2018-11-07 13:47:33 -0500
permalink:  carwash_application
---


This application connects the mobile detailers with people on the go looking for a carwash in crunch time situation or also for those enjoying a football game on a beautiful sunday with a detailer washing their car in the porch. I have had this idea for years and one of the reasons I started to learn to code was to work on this application. I realised people have to go to a carwash station and wait for the time their car is being take care of . In todays world with everything moving to services amazon prime delivering from anything to everything to the doorsteps then why not have a detailer with good rating and a very clean background come to your house and take care of dirty business. One more reason this can save time is lets say you are in a meeting and have to meet another potential client but have a messy car and do not want to make a bad impression on your client. Just click the button on your app and someone will come and take your car to the nearest carwash place and bring it back just in time for you to be ready to meet your client and make that big sale without any problems. How about your car being washed in the parking lot while you take care of groceries for the whole week. The detailer will have all the tools necessary to make sure a mint job is carried out with no compromise on the quality of work . Since it is a little risky to let a random person have full control of your vehicle but is not it what we do while we call an uber and take control of your life to a complete stranger. Sometime we have to take small risk in return for bigger rewards and the insurance companies take care of any losses in case there should be any. 

The carwash application is built in Rails framework and uses the MVC design pattern that divides an application into three inteconnected parts. The four models that take care of the complete working of the application for now are User, Car, Carwash and Detailer models. The User model makes new instances of users and  through active record associations has many cars , carwashes and detialers . It also runs validations on the user data like name and password to make sure only valid data is persisted in the database. The Car model makes cars that belong to a user and also has many carwashes. Validations make sure valid data is persisted in the database. The Carwash model is a joining model between User and the Detailer . The carwash belongs to a user and a detailer. Users have many detailers through carwashes and detailers have many users through carwashes. The Detailer model lets create the detailers but this part of the application is not been incorportated yet since people using the same application must be allowed to sign in as user or detailer and connect to the same carwash they were connected with . The detailer after the job is completed can go back home and look at the list of all the carwashes carried out during th day and leave a commment or rate the users . In the same way the user can leave a comment and a rating for the detailer on the quality of work done. I have plans to add this part of the application in the next update. 

There are four controller that inherit from the application_controller and each corresponds to the view with the create , read , update and delete features of the CRUD. The user can sign up with the credentials and also log in through external provider which in this case is Github. I used the [omniauth gem](https://github.com/omniauth/omniauth-github) and the steps provided make it very easy to install it. 
post on github for any help. You can sign in with external provider even without signing up and then later can change the password using the edit link on the show page. User can have multiple cars and can have multiple carwashes. On the index page the carwash history puts link to each carwash show page and the user has the ability to change the comment and rating of the detailer. On the same page there is another section that provides a list of all the carwashes that have not been commented yet. I used the scope method to make it work. It took me a while to figure out why the scope method as shown below was not giving me the desired list since I was expecting user_comment to be nil but what I learned from this exercise that even if you leave it empty the params (b) as shown below add the empty string even if you leave it empty. So I had to include both the nil and the "" (empty string) in the scope method (a)  to get the desired list of uncommented carwashes .

(a)

```
scope :uncommented, -> { where(user_comment: [nil, '']) }

```

(b)
```

{"utf8"=>"✓", "_method"=>"patch", "authenticity_token"=>"y9nRcK8vCW35x21ju0T14FX5oXcMrXVmiueuZq34yvWVEjq/q/l57gOyVVrYiQ0HX/TtGa1zxKr13YEy+4edIw==",
"carwash"=>{"page"=>"show", "user_rating"=>"3", **"user_comment"=>""}**, "commit"=>"Update Carwash", "controller"=>"carwashes", "action"=>"update", "user_id"=>"10", "id"=>"39"} permitted: false>

```
The new carwash instance is made with the user selecting the detailer based on their rating and the cost offered for the carwash. The cost is fixed now but down the road the detilaer will have the option to change it. The car is seleted from a radio button and then the app takes you to the show page where user can rate the carwash and leave a comment. All the carwashes are available in the history and available any time if the user may desire to look at them . 

I hope you found this blog informative and if you are interested in having a look at the code please go to the following
[https://github.com/waasifkhaan/CarWashApplink]









