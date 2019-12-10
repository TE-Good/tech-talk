# Project 3
# General Assembly Software Engineering : TechTalk

## Timeframe
7 Days

## Technologies Used
* JavaScript (ES6) / HTML5 / SCSS
* React.js
* Node.js
* Express
* MongoDB (NoSQL)
* Git / GitHub
* Mocha / Chai
* Heroku
* Skeleton CSS Framework
* Moment.js

## Overview
TechTalk was created in 7 days by a team of four developers; [@Vikram Bageja](https://github.com/vikram1510), [@Reema Patel](https://github.com/missreems), [@Sophie Turnell](https://github.com/sophieturnell), and I.

The concept of the project was to create a meet up website taliored towards developers. The website would allow you to host, as well as, attend events.

![front-page](https://i.imgur.com/6WgCqtd.jpg)

## Instructions
1. To register a profile, you can navigate to the register page and input the details you wish.
![register-page](https://i.imgur.com/Zzhx65v.jpg)
2. Log into the website through the login in page.
![login-page](https://i.imgur.com/oLOCGcW.jpg)
3. Search for an event you may be interested in. Making use of the filters to find specific events.
![events-page](https://i.imgur.com/Clt5Z6W.jpg)
4. Select an event, and click attend. You will be added to the list of attendees.
![show-page](https://i.imgur.com/Pytg7iJ.png)
5. If you click on your profile button, you will see that the event has been added to your events.
![profile](https://i.imgur.com/hHNEObJ.png)
6. To create an event, you can make one by navigating to the "CREATE" on the left nav bar. Once you create an event, this too will be on your profile.
![create-page](https://i.imgur.com/csxkLBO.jpg)


# Installation
Make sure to install all our package dependencies from our package-lock files via `$ yarn` before starting.

# Process
workshopped the idea 
First, as a team we sat down and workshopped ideas on what we could create. The decision was to create a meet up website, as this would offer all the CRUD calls for the events which would utilise what we had learnt previously.

We began the code as a team, with everyone all working on back end calls at a time and testing it through application Insomina. The back end was written in JavaScript, using Express, Mongoose, and Node.js. We worked like this for begining of the project, and then we wrote tests using the libraries Mocha and Chai for these routes. Over the weekend we set split the inital seeds duties, however these would need to be fleshed out properly later as our models changes slightly through the development.

Once the back end was in a good position we started on the front end, which was written using the React framework. I worked primarily on event page, form pages, and home page while pairing with others. On the event page, there were a few features that we worked through which were using a package called React-Select that allowed for great aesthetics for the dropdown form, Moment.js was used for the dropdown filter on the event time/date, and Mapbox was used for the mapping that displayed all the event locations and to translate written addresses into co-ordiinates.

The form pages (Register, Login, Settings) had a similar format and to keep a consistant style thoughout we decided to use the Skeleton CSS Framwork which gave good looking buttons and simple dropdown lists.


```javascript
componentDidMount() {
    this.latlongCalc()
  }

  latlongCalc() {
    this.props.events.map(event => {
      axios.get(`https://api.mapbox.com/geocoding/v5/mapbox.places/${event.location}.json?access_token=${process.env.MAPBOX_ACCESS_TOKEN}`)
        .then(res => {
          const lat = res.data.features[0].geometry.coordinates[1]
          const long = res.data.features[0].geometry.coordinates[0]
          const _id = event._id
          const category = event.category

          this.setState({ latLongs: [...this.state.latLongs, { _id, lat, long, category }] })
        })
        .catch(err => console.log(err))
    })
  }
```
*Mapbox's API query to parse a string of a location into latitude and longitude numbers.*

# Challenges
Ensuring a consistant design throughout the website was difficult when you had different people styling different pags. To get around this, we had to really sit down and illustrate what we all were envisioning and made sure we all compromised so that a group aesthitic was achieved. Additionally, as a team we took inspiration from other websites to give examples of our ideas. This gave better context, and meant we could see the style easier.

# Wins
Mapbox was a bit daunting at first to use, as there was two differing documentation to use and it could be quite extensive. However, Mapbox wasn't much of a problem for the team and I. Together we were able to handle the mapping easily, and I was happy with our results.

Likewise with Express as a team we were not as familiar with the framwork, but we were able to encourage and help each other out in the back end coding.

# Further features
If we had more time on this project, I would have liked to have made the website more responsive; down to a mobile phone level. Secondly, adding notifications on upcoming events, and adding a forum would have been interesting.