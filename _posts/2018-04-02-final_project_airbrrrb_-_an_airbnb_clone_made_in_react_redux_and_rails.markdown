---
layout: post
title:      "Final Project: Airbrrrb - An Airbnb Clone made in React, Redux, and Rails"
date:       2018-04-02 13:31:59 -0400
permalink:  final_project_airbrrrb_-_an_airbnb_clone_made_in_react_redux_and_rails
---


For my final project I decided to create an airbnb clone to showcase all of the knowledge I have made so far in the 8 months I have spent here at Flatiron. 

To start this project I began by building out my API Endpoints and my React Component Hierarchy.

API Endpoints

## Root

GET '/'

## JSON API

### Users

GET '/api/users'
POST '/api/users'
GET '/api/users/:id'
PATCH '/api/users/:id'

### Venues

GET '/api/venues'
POST '/api/venues'
GET '/api/venues/:id'
PATCH '/api/venues/:id'
DELETE '/api/venues/:id'

### Bookings 

GET 'api/bookings'
POST 'api/bookings'
GET '/api/bookings:id'
DELETE '/api/bookings/:id'

### Reviews

GET '/api/reviews'
POST '/api/reviews'
GET '/api/reviews/:id'
DELETE '/api/reviews/:id'

Component Hierarchy

### Main Page

- App (div)
    - Header
        - **SearchContainer**
            - Search
        - Nav
    - Main (div)
        - ** VenueContainer**
            - VenueFilter
            - VenueList
                - VenueItem

### Venue Page
- App (div)
    - Header (already created on main page)
    - Main (div)
        - **VenueShowContainer**
        - Images
        - Description
        - Reviews
        - HostInfo
        - Location
        - BookingForm
        - 
### User Profile Page
- App (div)
- Header (already created on main page)
- Main (div)
    - ** UserContainer**
    - UserInfo
    - Reviews


