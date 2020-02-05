---
layout: post
title:      "My First CLI Gem "
date:       2020-02-02 23:41:04 -0500
permalink:  my_first_cli_gem
---


My first project assignment here at Flatiron was to build a CLI gem that also demonstrates scraping information from the internet using Nokogiri. I decided to create a gem that returns langauges that are spoken in a country selected by the user. I chose to do this because I am very interested in languages and I am pretty active in the polyglot space of the internet. The website that I scraped information from is the [World Factbook](https://www.cia.gov/library/publications/the-world-factbook/) and last but not least, the name of my gem is Babbel Explorer.

## Getting Started

I created Babbel Explorer from scratch so, I had to first figure out where to start. I watched several videos and took notes about how I wanted my gem to be set up. Once I had a pretty solid idea about what to do, I went ahead and ran `bundle gem babbel_explorer` from the terminal in VScode and got started. This provided me with a sort of 'template' of folders and files. I also followed some other steps from the "Eden Events" videos that are on Learn Instruct. 

## Writing the Code

### ./bin
This folder contains babbel_explorer which is the executable file to run the app. I also incuded a shebang line in this file so that so user doesn't have to explicitly call the Ruby interpreter.

### ./lib 
This folder contains my classes and babbel_explorer.rb which is used for my environment requirements. It also contains version.rb which states the version of the app.

### Classes
I orignally thought that I would have 4 classes; CLI, Scraper, Country, and Language. I later decided I didn't need a Language class since I could scrape that information at the same time as the country information and just push it into an array in my Country class when initializing a country, so I deleted it. Now, I just have 3. 

#### cli.rb
This is where my CLI class lives. It is responsible for running the app, getting user input, displaying information collected by the Scraper....

#### scraper.rb
The Scraper class is responsible for getting the country and langauge information from the source page and giving it to the Country class....

#### country.rb
The Country class is responsible for initializing countries with the information that was scraped and then saving them in an array.




## The Flow

1. When the user runs the app, the call method puts out a greeting and then calls the menu method.

2. The menu method gives the options to view the country list or to exit. If the user input is invalid*, an error message is displayed and the menu is puts out again. 

3. If the user chooses to view the country list, the explore method is called. The explore method calls get_countries, country_list, and get_selection until the user types exit.  

4. The get_countries method has all the scraped data ready to be used.

5. country_list lists the countries and the user selects a country by its corresponding number.

6.  get_selection calls validates the user input and then calls show_language_blurb of the selected country.

7. show_language_blurb displays the language information that was retrieved by the scraper and then gives the user the option to quit or to select another country from the list.

8. explore_more confirms if the user is done using the app but also gives the option the view the country list again.

9. exit displays a thank you message and then closes the app.


*I made an invalid_input method because I was going to use it more than once however, I changed my code. I did decide to keep it though because I may need it in the future when I add to this gem. I also made a seperate method for validating input but decided not to use it at this time.


## The future of Babbel Explorer
I do plan to add a few things to this gem and publish it to rubygems.org. I would like to be able to give the user the option to view countries by region.  I would also like to be able to give the user an option to choose a language and see the countries that it is spoken in (according to the source page, of course).

That's all for now. Feel free to check this repo out on GitHub [here](https://github.com/abrolon87/babbel_explorer_cli_gem).  








