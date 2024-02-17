# WAPH-Web Application Programming and Hacking

## Instructor: Dr. Phu Phung

**Name**: Reshma Reddy Vallakonda

**Email**: vallakry@mail.uc.edu

*Short-bio*: Reshma Reddy Vallakonda is a UC Student who is interested in Front-end Web Development. 

![headshot](headshot.jpeg)

## Repository Information

Respository's URL: git@github.com:reshmareddy2709/waph-vallakry.git

This is a private repository for Reshma to store all code from the course.

# Individual Project 1 – Front-end Web Development with a Professional Profile Website on github.io cloud service

## Overview and Requirements 

For the Individual Project 1, I developed a professional profile website and deployed it on GitHub Pages. The website serves as a showcase of my resume, skills, and experiences, while also incorporating various technical functionalities like integrating joke API, digital clock, analog clock, show my email id, weather API and Flag counter. The main objectives of this project were to enhance my front-end web development skills and gain practical experience in deploying websites using GitHub Pages.

The link to access my website is: [https://sheelada.github.io/index.html](https://sheelada.github.io/index.html).

The link to access Individual Project-1 is: [https://github.com/sheelada/sheelada.github.io](https://github.com/sheelada/sheelada.github.io).

## General Requirements

### Personal Website on Github.io

I created a new public repository with the name `sheelada.github.io`. Created a personal website on GitHub Pages featuring my resume, contact information, education, experiences, projects, certifications and skills.

The link to access my website is: [https://sheelada.github.io/index.html](https://sheelada.github.io/index.html).

![Portfolio Website](images/screenshot1.png)

### "Web Application Programming and Hacking" course and related hands-on projects on waph.html file

I created the separate page with the name waph.html on my repository introducing the "Web Application Programming and Hacking" course and its related hands-on projects. In this I includes overviews of Lab0, Lab1, Lab2, Hackathon 1 and Individual Project 1. 

The link to access waph.html is: [https://sheelada.github.io/waph.html](https://sheelada.github.io/waph.html).

This page link is accessible from the personal website as shown in below screenshot:

![waph.html page link on website](images/screenshot2.png)

![waph.html page](images/screenshot3.png)

## Non-technical requirements

### Bootstrap Template

I have downloaded a bootstrap template from the website `https://bootstrapmade.com/` 

I changed the template as per my requirements and tasks given by the professor

### Page Tracker

I Integrated Flag Counter as a page tracker to monitor website visits and engagement. 

From the two given websites. I have chosen `https://flagcounter.com/`. I generated a key from the website and integrated it in my code. Flag counter is visible in my website homepage as integrated.

Code for integrating Flag Counter:

```html
<div style="text-align:left;">
    <a href="https://info.flagcounter.com/szVl"><img
        src="https://s11.flagcounter.com/count2/szVl/bg_FFFFFF/txt_000000/border_000000/columns_2/maxflags_10/viewers_0/labels_1/pageviews_1/flags_0/percent_0/"
        alt="Flag Counter" border="0"></a>
</div>
```

![Flag Counter](images/screenshot4.png)



## Technical requirements

### A digital clock; An analog clock; show/hide your email:

Same as lab 2, Implemented a digital clock and an analog clock using JavaScript to display current time and also added functionality to show/hide the email address based on user interaction.

Source Code for digital clock:
```JS
function displayTime() {
          document.getElementById('digital-clock').innerHTML = "current time:" + new Date();
        }
        setInterval(displayTime, 500);
```

Source Code for Analog clock:
```JS
var canvas = document.getElementById("analog-clock");
        var ctx = canvas.getContext("2d");
        var radius = canvas.height / 2;
        ctx.translate(radius, radius);
        radius = radius * 0.90
        setInterval(drawClock, 1000);

        function drawClock() {
          drawFace(ctx, radius);
          drawNumbers(ctx, radius);
          drawTime(ctx, radius);
        }
```

Source Code for show/hide your email:

```JS
function showhideEmail() {
      if (shown) {
        document.getElementById('email').innerHTML = "Click here to show my email";
        shown = false;
      }
      else {
        var myemail = "<a href='mailto:sheelada" + "@" + "mail.uc.edu'>sheelada" + "@" + "mail.uc.edu</a>";
        document.getElementById('email').innerHTML = myemail;
        shown = true;
```

Screenshot Showing Digital clock, Analog Clock, Show/hide your email:

![Digital clock, Analog Clock, Show/hide your email](images/screenshot5.png)


### One more Functionality of my choice

I have integrated Hacker News Api using `VUE.JS` Framework. This Api displays 5 HACKER NEWS TRENDING ARTICLES. 

Source code for Haacker news Api:
```JS
<script src="https://cdn.jsdelivr.net/npm/vue@2"></script>
```
 ```JS
new Vue({
el: '#app',
data: {
  articles: []
},
mounted() {
  this.fetchArticles();
},
methods: {
  fetchArticles() {
    fetch('https://hacker-news.firebaseio.com/v0/topstories.json')
      .then(response => response.json())
      .then(ids => {
        // Take only the first 10 article IDs
        ids = ids.slice(0, 5);
        // Fetch details of each article
        Promise.all(ids.map(id =>
          fetch(`https://hacker-news.firebaseio.com/v0/item/${id}.json`)
            .then(response => response.json())
        ))
          .then(articles => {
            // Update articles data
            this.articles = articles;
          });
      })
      .catch(error => console.error('Error fetching articles:', error));
  }
}
});
 ```
![5 Hacker news trending articles](images/screenshot6.png)

### Joke API

Integrated the jokeAPI to fetch a new joke every minute and display it on the website.

Source code for Joke API:

```JS
function fetchJoke() {
          $.get("https://v2.jokeapi.dev/joke/Any?type=single", function (result) {
            console.log("From jokeAPI: " + JSON.stringify(result));
            if (result && result.joke) {
              $("#joke").text("Here's a joke for you: " + result.joke);
            } else {
              $("#joke").text("Could not retrieve a joke at the moment.");
            }
          });
        }

fetchJoke();
setInterval(fetchJoke, 60000);
```

### Weather API

Integrated the Weatherbit API to fetch current weather information for Cincinnati and display it on the website.

```JS

$(document).ready(function () {
// Fetch data from Weatherbit API
$.getJSON("https://api.weatherbit.io/v2.0/current?city=cincinnati&key=08d6dd69bae245f081687c17710408a2", function (data) {
  // Extract relevant weather information
  var temperature = data.data[0].temp;
  var description = data.data[0].weather.description;
  var iconCode = data.data[0].weather.icon;

  // Update weather information
  $("#weather-info").text("Current Temperature: " + temperature + "°C, Weather: " + description);

  //update weather icon
  $("#weather-icon").attr("src", "https://www.weatherbit.io/static/img/icons/" + iconCode + ".png");
  $("#weather-icon").attr("alt", description);
});
});

```

![Joke API and weather API](images/screenshot7.png)

### Javascript Cookies

Implemented JavaScript cookies to remember the client's visit and display personalized messages based on whether they are a first-time visitor or returning user. For first time visit it shows "Welcome to my homepage!", for returning user it displays "Welcome back! Your last visit was (last visit time and date)".

```JS
// Function to set or retrieve the value of a cookie
function setCookie(name, value, days) {
var expires = "";
if (days) {
  var date = new Date();
  date.setTime(date.getTime() + (days * 24 * 60 * 60 * 1000));
  expires = "; expires=" + date.toUTCString();
}
document.cookie = name + "=" + (value || "") + expires + "; path=/";
}

function getCookie(name) {
var nameEQ = name + "=";
var ca = document.cookie.split(';');
for (var i = 0; i < ca.length; i++) {
  var c = ca[i];
  while (c.charAt(0) === ' ') c = c.substring(1, c.length);
  if (c.indexOf(nameEQ) === 0) return c.substring(nameEQ.length, c.length);
}
return null;
}

// Function to display the welcome message
function displayWelcomeMessage() {
var lastVisit = getCookie("lastVisit");
if (!lastVisit) {
  // First-time visit
  setCookie("lastVisit", new Date().toISOString(), 30); // Set cookie to expire in 30 days
  alert("Welcome to my homepage!");
} else {
  // Returning visit
  var lastVisitDate = new Date(lastVisit);
  alert("Welcome back! Your last visit was " + lastVisitDate.toLocaleString());
}
}

// Call the function when the page loads
window.onload = displayWelcomeMessage;

```
![Fisrt visit](images/screenshot8.png)
![revisit cookies](images/screenshot9.png)
















