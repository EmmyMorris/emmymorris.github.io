---
layout: post
title: Sweater Weather
subtitle: Weather Forcast API
cover-img: /assets/img/leaves.jpg
thumbnail-img: /assets/img/leaves.jpg
gh-repo: EmmyMorris/sweater-weather
gh-badge: [star, fork, follow]
tags: [Rails, RSpec, ReST API, Authentication and Authorization]
comments: true
---
**About**

Sweater Weather is a API to plan road trips! This API will allow users to see the current weather as well as the forecasted weather at the destination.

### End Points

###### Forecast

- GET /api/v1/forecast
- Get forcast for location PATH PARAMETERS- :location(string)- REQUIRED

- Example request:
  -  GET /api/v1/forecast?location=denver,co
  - Content-Type: application/json
  - Accept: application/json

- Example response:

~~~
{
 "data": {
   "id": null,
   "type": "forecast",
   "attributes": {
     "current_weather": {
       "datetime": "2020-09-30 13:27:03 -0600",
       "temperature": 79.4,
       etc
     },
     "daily_weather": [
       {
         "date": "2020-10-01",
         "sunrise": "2020-10-01 06:10:43 -0600",
         etc
       },
       {...} etc
     ],
     "hourly_weather": [
       {
         "time": "14:00:00",
         "conditions": "cloudy with a chance of meatballs",
         etc
       },
       {...} etc
     ]
   }
 }
}
~~~
---

###### Backgrounds

- GET /api/v1/backgrounds
- Get a background PATH PARAMETERS- :location(string)- REQUIRED

- Example request:
  - GET /api/v1/backgrounds?location=denver,co
  - Content-Type: application/json
  - Accept: application/json

- Example response:

~~~
{
   "data": {
       "id": null,
       "type": "background",
       "attributes": {
           "id": null,
           "location": "denver,co",
           "image_url": "https://images.unsplash.com/photo-1619856699906-09e1f58c98b1?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=MnwyNTI1ODV8MHwxfHNlYXJjaHwxfHxkZW52ZXIlMkNjb3xlbnwxfHx8fDE2Mjg2NTE2MTg&ixlib=rb-1.2.1&q=80&w=1080",
           "credit": {
               "source": "unsplash.com",
               "author": "rdehamer",
               "logo": "https://images.unsplash.com/profile-1577912636161-6a3ada136470image?ixlib=rb-1.2.1&q=80&fm=jpg&crop=faces&cs=tinysrgb&fit=crop&h=64&w=64"
           }
       }
   }
}
~~~
---

###### Users

- POST /api/v1/users
- Create a user

- Example request:
  - POST /api/v1/users
  - content-Type: application/json
  - Accept: application/json

~~~
{
 "email": "whatever@example.com",
 "password": "password",
 "password_confirmation": "password"
}
~~~

- Example response:

~~~
{
 "data": {
   "type": "users",
   "id": "1",
   "attributes": {
     "email": "whatever@example.com",
     "api_key": "jgn983hy48thw9begh98h4539h4"
   }
 }
}
~~~
---

###### Sessions

- POST /api/v1/sessions
- Creates a session

- Example request:
  - POST /api/v1/sessions
  - Content-Type: application/json
  - Accept: application/json

~~~
{
 "email": "whatever@example.com",
 "password": "password"
}
~~~

- Example response:

~~~
{
 "data": {
   "type": "users",
   "id": "1",
   "attributes": {
     "email": "whatever@example.com",
     "api_key": "jgn983hy48thw9begh98h4539h4"
   }
 }
}
~~~
---

###### Road Trips

- POST /api/v1/road_trip
- Get a route given two locations PATH PARAMETERS- :origin(string)- REQUIRED, :destination(string)- REQUIRED

- Example request:
  - POST /api/v1/road_trip
  - Content-Type: application/json
  - Accept: application/json

~~~
{
 "origin": "Denver,CO",
 "destination": "Pueblo,CO",
 "api_key": "jgn983hy48thw9begh98h4539h4"
}
~~~

- Example response:

~~~
{
 "data": {
   "id": null,
   "type": "roadtrip",
   "attributes": {
     "start_city": "Denver, CO",
     "end_city": "Estes Park, CO",
     "travel_time": "2 hours, 13 minutes"
     "weather_at_eta": {
       "temperature": 59.4,
       "conditions": "partly cloudy with a chance of meatballs"
     }
   }
 }
}
~~~
