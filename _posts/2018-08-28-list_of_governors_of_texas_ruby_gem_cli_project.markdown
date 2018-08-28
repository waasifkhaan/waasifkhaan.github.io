---
layout: post
title:      "List of Governors of Texas : Ruby Gem CLI Project"
date:       2018-08-28 22:47:08 +0000
permalink:  list_of_governors_of_texas_ruby_gem_cli_project
---


This project initially seemed like a game of Tennis where the serve is the biggest challenge and you cannot get far without getting the first part right. Getting the initial set up right in the learn environment was the biggest challenge as I got used to the TDD format and did not have enough knowledge on how to set up everything from scratch. After seeing a couple of videos on using bundler to make gems I finally started the project on scraping data  from the wikipedia page ( https://en.wikipedia.org/wiki/List_of_Governors_of_Texas )  for the governors who have served the state of Texas since 1846. 

The project consists of the Scraper, Governor and CLI classes and the namespace convention was used to avoid any conflict with the Ruby defaulf classes if any. With the namespace convention the scraper class is named as TexasGovernorCliApp::Scraper. I used the nokogiri gem to scrape data from the abovementioned page and the trickiest part was to get data from the table as there are rows , columns and headers involved. Even the rows are further divided into more rows which sent me in a loop for days. With hit and trial method I was able to get the correct number of objects in the array  for further analysis. Each object was further worked on to get the needed details for each governor like full name , age , party affiliation, term in office and a URL for the respective wikipedia page. The scraper class is responsible for making hashes for each governor with the desired attributes and then the Governor class with the help of the "send" method converts them in objects and saves it in the self.all class method for use in the CLI class. 

Below is an example of the properties saved in the self.all class method in the TexasGovernorCliApp::Governor class for each object 

Greg Abbott
Republican Party
Age: November 13, 1957(Age60 Years)
Term in Office: January 20, 2015–Incumbent
https://en.wikipedia.org/wiki/Greg_Abbott

The CLI class is responsible for interacting with the user and providing the different options after displaying the welcome message. The user has 4 options to choose from and the application provides results based on the selected choice as shown above. After every query the user is taken back to the main page to either request more information or exit the program. On exiting the user is greeted with a goodbye message. 

The application was running slow since I was calling methods from the scraper class in the CLI class and everytime user goes back to the main menu and request more details about another governor the whole scraping process would run again. To make the application run faster I called the "create_from_collection" method once while the CLI class is instantiated and then the application reads data from the Governor class self.all method. 

def call 
    TexasGovernorsCliApp::Governor.create_from_collection
    start
end 

Please look at the repository at https://github.com/waasifkhaan/texas_governors_cli_app to get a clear picture of the code in all the classes.

Overall this project offered me a great challenge to independently work on a project from scratch. The open ended nature of the project made me think about all the options available and now on completion I feel alot more confident with my programming skills and ready to take on any challenge that may come along the way.  

It seemed very difficult in the beginning but with each step the working of the application became more clear and the light at the end of the tunnel got brighter by the day. I loved coding in this project and want to continue working on this application to include governors from all the states of the United States and let the user choose the state first and then get details for all the honourable governors from respective states. 





