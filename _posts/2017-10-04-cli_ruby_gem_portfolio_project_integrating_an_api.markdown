---
layout: post
title:      "CLI Ruby Gem Portfolio Project: Integrating an API "
date:       2017-10-04 16:32:24 -0400
permalink:  cli_ruby_gem_portfolio_project_integrating_an_api
---

## **Intro**

When you’re developing past the beginner level in Ruby, you will reach a point where you come across an HTTP API that doesn’t have a gem available. While creating my Weatherbot Ruby Gem I opted to use an API instead of scraping data from a website, since as far as I understood it, they were almost similar conceptually, with the API route having some documentation to help guide you, as well as undertaking the learning curve of learning how to manipulate API data. I was told by the section lead Corinna that as a developer you will have to create your own API interfaces, so it seemed most advantageous to start now.
## **Choosing the right API**
There are **many** weather related API's. To be honest, I had no clue which one was the most accurate, I just scoped out a few after googling 'weather API' that satisfied a few requirements in order to get this project completed without hating myself halfway through. I needed the API to:

1. Be beginner friendly
2. Have clear, concise documentation
3. Manipulate data easily
4. Free to start developing
5. Be accurate in its reporting

I was disappointed to find out some of the more popular ones had very limited free developer tiers for their data. Since I am relatively new to API's, I decided that OpenWeatherMap's API had the best mix of the above requirements. 

To be honest, it is hard to fully review the 1st substantial API you're using with no other's to compare it to. The learning curve was great, many hours were spent in pry breaking down hashes of hashes, but overall I was quite satisfied with my choice since I was ultimately able to complete the project without too much headache.

When I started, I was really tempted to go searching for a different API to use instead, eventually I got the hang of the way I was requesting data, and thankfully OpenWeatherMap had solid documentation that made the data useful to implement.

## **HTTParty Time**
I was told in a CLI Gem study group to use the HTTParty gem to allow Ruby to parse the response of the location I was requesting. If you're using Bundler, it’s easy to get started with HTTParty. Just add `spec.add_development_dependency "httparty", "~> 0.0"` to your .gemspec file, and `require 'httparty'` in your Ruby environment file, and you’re ready to go. 

If you want more info about Bundler, they’ve got a great site with all sorts of helpful information about how to get up and running at https://bundler.io.

If you’re not using Bundler, you can run gem install httparty to get HTTParty installed. You’ll want to add require 'httparty' where appropriate to include it into your scripts.

HTTParty encapsulates HTTP. The HTTParty module exposes all of the normal HTTP request methods, such as GET, POST, PUT, and DELETE. So, for example, you can make a GET request to a URL with the following code:

```
response = HTTParty.get("https://api.openweathermap.org/data/2.5/weather?q=<location>&appid=<appid>&units=imperial")
```

The object returned from HTTParty.get is an HTTParty::Response object containing the JSON that was returned from the site, along with its headers and other methods relating to the HTTP protocol. One of the most useful features of HTTParty is that it automatically parses JSON and XML responses, based on the Content-Type of the response, so as soon as your response comes back it’s ready for you to work with it:

```
parsed = response.parsed_response

=> {"coord"=>{"lon"=>-74.01, "lat"=>40.71},
 "weather"=>
  [{"id"=>800,
    "main"=>"Clear",
    "description"=>"clear sky",
    "icon"=>"01d"}],
 "base"=>"stations",
 "main"=>
  {"temp"=>74.77, "pressure"=>1026, "humidity"=>44, "temp_min"=>69.8, "temp_max"=>78.8},
 "visibility"=>16093,
 "wind"=>{"speed"=>4.7, "deg"=>230},
 "clouds"=>{"all"=>1},
 "dt"=>1507144500,
 "sys"=>
  {"type"=>1,
   "id"=>1969,
   "message"=>0.1678,
   "country"=>"US",
   "sunrise"=>1507114602,
   "sunset"=>1507156286},
 "id"=>5128581,
 "name"=>"New York",
 "cod"=>200}
```

OK, not too bad, time to actually get started on extrapolating this data into a readable format, and setting up my CLI interface to interact with it.

## **Building out the gem structure**
The most daunting point of this project aside from choosing the API, was knowing where to go from a blank slate. Thankfully, I decided to watch and code along with this [video walkthrough](https://www.youtube.com/watch?v=_lDExWIhYKI), narrated by Flatiron School's absurdly knowledgable dean Avi Flombaum. I hope to be able to build code and describe it effortlessly like this, but for now, this blog post will have to suffice.

## **CLI Controller logic**
I planned to make this my 1st Ruby gem when I started the project, and basically followed the video walkthrough for the first 45 minutes or so to get the file structure, and essential 'stubs' of my code in order to move forward. I highly suggest it, and even though he scrapes two websites with Nokogiri, I found the structure of the placeholder code to be essential to building out my classes, methods, & CLI structure.

After running the commands in the video, I had my gem structure ready to build out the CLI interface. The hardest part was being able to anticipate how nested I wanted my data to be, and how to access it. I initially thought of having a list of cities, but found that the API was incredibly robust in returning a location query. So over time, I decided to just have a prompt where I asked for a location, and then gave the user the option of typing 'map' to open the coordinates in Google Maps, and 'forecast' to give a 3 day forecast based on what the API returned.

## **API class**
This is where things started to get interesting. I was in uncharted waters here, I basically took what I had learned from the lessons, and looked at many other peoples projects to see how they structured their 'scraper', or in my case 'API' class in order to manipulate all of this data that was being returned to me.

I started by creating a class method in order to encapsulate all of the attributes of the current weather object I was creating. This is where it was easy to get lost in all of the data I was working with. Thankfully the API documentation was concise and to the point, so once I was able to parse through response data in a straightforward manner. Looking at my code you might think otherwise since in order to make this an **object**, not a simple hash, I needed to set up my proper attr_accessors and read all of the fun Error messages Ruby would return to me.

Now that I have finished a fully working, and somewhat organized version, I will definitely be separating my API class into other parts for readability purposes.

I found that committing often, and updating code in small increments, resulted in the most constructive process. I had to keep reminding myself to commit often, and give thoughtful commit messages in order to show my progress. This also had the advantage of rolling back small code changes that would quickly make this project difficult to code out at times.

## **Helper class**
I ended up coding out this separate class to get used to inheriting class methods from other classes. It is nothing substantial, but did show a separation of concerns for my code, and also made sense since these methods were just helpers to some calculations: wind_direction, and FahrenheitToCelsius.

## **Forecast method, soon to be its own class**
Easy enough by now, right? Well, actually viewing this response data in the pry console for the 5 day / 3 hour forecast left me more like: 

![](https://img.gifmagazine.net/gifmagazine/images/962539/original.gif?1477399942)

This is where I had to make some substantial compromises in my code structure. I had planned on giving 3 hour sections, but at my current level, found no reasonable way to harness all of this data without having to hardcode some of it in. I settled for 3 days at 24 hour intervals, which leaves this project open to adding new functionality in the future.

Unfortunately, this API gave me forecast data in 3 hour section hashes, totalling **40** hashes with a dozen keys and values per hash for a 5 day period. For the sake of getting this project done, I thought that getting working and submitted was more important than implementing a feature I knew would be impressive to nobody in its current form.

## **Wrapping up**
I am now at the final steps in submitting this gem to being publicly listed on RubyGems.org. I hope that it serves a purpose to someone, somewhere in the Ruby world. I found this project to be very thought provoking, and found myself exploring many methods in pry that I never would have tried. I managed to finish this project in 7 working days from conception to submission. I am looking forward to the next projects and definitely feel like I have learned a lot about finally building a standalone application.

My projects' [Github repo](https://github.com/TheInvalidNonce/weatherbot-cli-app)

OpenWeatherMap's API can be found [here](http://openweathermap.org/api)
