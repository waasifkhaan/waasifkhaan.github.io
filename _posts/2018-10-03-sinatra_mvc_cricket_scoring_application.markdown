---
layout: post
title:      "Sinatra MVC Cricket Scoring Application"
date:       2018-10-04 00:31:29 +0000
permalink:  sinatra_mvc_cricket_scoring_application
---

Having played the game of Cricket for around 20 years , this project got me working in my dreams  since it gave me an opportunity to apply the tools I learned from the lessons / labs but also express the love of the game in a completely new way I had never experienced before. 

Cricket is a game played between two teams of eleven players each and is very similar to Baseball. The idea is to hit the ball out of the park or just tap to get runs. Here is a link to the a video on youtube for a brief description of the game.  https://www.youtube.com/watch?v=AqtpNkMvj5Y . Team scoring more runs wins the game. Since I play this game professionally and am part of a Club in the Austin / Houston area. I structured the models in the application exactly how they are in the real world. Each Club has many teams and then each team has many players. A game model is also incorporated which has to have two teams to participate to make it a game. In each game each of the eleven players can score runs so I have a join table that has a game_id and player_id and also has an attribute of "run". 

I used Corneal gem to generate the app MVC strutcture with basic styling and environment already set up for you. User model lets you create a user and login with the valid credentials only. The exceptions are raised and displayed on the page in a red font. User can create a game , add a team, add a player and update / delete games only created by them. The options do not appear in show page if a different user tries to look at the game scorecard. Little coding patch in the show.erb you can get this to work since the game .user_id must match the current_user to be able to edit or delete the  game. On the index page the user can see all the games or their own games. Games have different attribute type like hometeam, awayteam, toss , result and then each player has runs through the score class. The application meets the CRUD  requirement of the project since the user is able to create, read , update and destroy the games created by them or read the games created by different users. Link to my Github for this project provides all the coding and structure of this app since I do not want to take up space with images and codes that can be seen here  https://github.com/waasifkhaan/sinatra-project-cricket-scoring-app. 

There are three controller that inherit from the application_controller and each corresponds to the view with the create , read , update and delete features of the CRUD.

I have done some basic styling on top of what came with the Corneal gem. I highly recommend using this gem to create any Sinatra application as it will save you alot of time setting up the environment that comes built in with the app. 

Completing this project I feel accomplished to have made an applicaiton that rhymes with the sports I love . The project being open-ended gave me enough to think about building this app from scratch. Since I knew how the models ( Club, Team, Game, Player , User) relate to each other it was easy going for me but I suggest the main part of this project is to understand how the models are related and how the has_many and belongs_to relationship are set up . Based on that set up the database tables and its pretty much downhill from then on. Do spend more time on understanding the relationship before going on to work on the controllers.  



