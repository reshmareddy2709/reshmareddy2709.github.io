# WAPH-Web Application Programming and Hacking

## Instructor: Dr. Phu Phung

**Name**: Reshma Reddy Vallakonda

**Email**: vallakry@mail.uc.edu

*Short-bio*: Reshma Reddy Vallakonda is a UC Student who is interested in Front-end Web Development. 

![headshot](headshot.jpeg)

## Repository Information

Respository's URL: [git@github.com:reshmareddy2709/waph-vallakry.git](git@github.com:reshmareddy2709/waph-vallakry.git)

This is a private repository for Reshma to store all code from the course.

# Individual Project 1 – Front-end Web Development with a Professional Profile Website on github.io cloud service

## Overview and Requirements 

For my first individual project, I created a professional profile website and hosted it on GitHub Pages. This website serves as a display for my resume, skills, and experiences. Additionally, it includes various technical features such as integrating a joke API, digital and analog clocks, displaying my email ID, weather API, and a flag counter. The main objectives of this project were to improve my skills in front-end web development and gain hands-on experience in deploying websites using GitHub Pages.

You can access my website through this link: [https://reshmareddy2709.github.io/Project1/index.html](https://reshmareddy2709.github.io/Project1/index.html)

To explore the Individual Project-1 repository, you can visit:[https://github.com/reshmareddy2709/reshmareddy2709.github.io](https://github.com/reshmareddy2709/reshmareddy2709.github.io)
## General Requirements

### Personal Website on Github.io

I made a new public repository called sheelada.github.io and built a personal website on GitHub Pages. The website includes sections for my resume, contact details, education, experiences, projects, certifications, and skills.

Here's the link to check out my website: [https://reshmareddy2709.github.io/Project1/index.html](https://reshmareddy2709.github.io/Project1/index.html)


![Portfolio Website](img1.png)
![Portfolio Website](img2.png)
![Portfolio Website](img3.png)

### "Web Application Programming and Hacking" course and related hands-on projects on waph.html file

I added a separate page named waph.html to my repository, providing information about the "Web Application Programming and Hacking" course along with details about associated hands-on projects like Lab0, Lab1, Lab2, Hackathon 1, and Individual Project 1.

You can view the dedicated page here: [https://reshma2709.github.io/Project1/waph.html](https://reshma2709.github.io/Project1/waph.html).

![waph.html page](img4.png)
![waph.html page](img5.png)
![waph.html page](img6.png)

![link in index to show waph](img7.png)

## Non-technical requirements

### Bootstrap Template

I downloaded a Bootstrap template from https://bootstrapmade.com/ and customized it according to my needs and the tasks assigned by my professor.

### Page Tracker

I incorporated a Flag Counter as a page tracker to monitor visits and engagement on my website. I chose https://flagcounter.com/ for this purpose. To implement it, I generated a key from the website and integrated it into my code. You can see the Flag Counter visibly displayed on my website homepage.

Here is the code I used to integrate the Flag Counter:

```html
<div style="text-align:left;">
    <a href="https://info.flagcounter.com/szVl"><img
        src="https://s11.flagcounter.com/count2/szVl/bg_FFFFFF/txt_000000/border_000000/columns_2/maxflags_10/viewers_0/labels_1/pageviews_1/flags_0/percent_0/"
        alt="Flag Counter" border="0"></a>
</div>
```

![Flag Counter](img8.png)



## Technical requirements

### A digital clock; An analog clock; show/hide your email:

Similar to Lab 2, I implemented a digital clock and an analog clock on my website using JavaScript to showcase the current time. Additionally, I added functionality to dynamically show or hide the email address based on user interaction.

The JavaScript code for the clocks and email address functionality is as follows:
Source Code for digital clock:
```JS
<div id="digit-clock"></div>
    <script>
    function displayTime() {
        document.getElementById('digit-clock').innerHTML = "Current time: " + new Date();
    }
    setInterval(displayTime, 500);
    </script>
```

Source Code for Analog clock:
```JS
</div>
    <canvas id="analog-clock" width="150" height="150" style="background-color:#999"></canvas>
    <script src="https://waph-uc.github.io/clock.js"></script>
    <script>
        var canvas = document.getElementById("analog-clock");

        var ctx = canvas.getContext("2d");

        var radius = canvas.height / 2;

        ctx.translate(radius, radius);
        radius = radius * 0.9;

        setInterval(drawClock, 1000);
        function drawClock() {
            drawFace(ctx, radius);

            drawNumbers(ctx, radius);

            drawTime(ctx, radius);
        }
            </script>
```
![Digital clock, Analog Clock](img9.png)

Source Code for show/hide your email:

```JS
<p id="email" onclick="showhideEmail()">Show my email</p>
     <script>
        var shown = false;

        function showhideEmail() {
            if (shown) {
                document.getElementById("email").innerHTML = "Show my email";
                shown = false;
            } else {
                var myemail =
                    "<a href='mailto:devanaoy" +
                    "@" +
                    "ucmail.uc.edu'>devanaoy" +
                    "@" +
                    "ucmail.uc.edu</a>";
                document.getElementById("email").innerHTML = myemail;
                shown = true;
            }
        }
    </script>
```

![show/hide email](img11.png)


### One more Functionality of my choice

I successfully incorporated the Hacker News API into my website using the Vue.js framework. This integration enables the display of the top 5 trending articles from Hacker News.

Source code for Haacker news Api:
```JS
<button id="toggleBtn">Toggle Text</button>
<p id="toggleText" style="display: none;">Hello, world!</p>

<script>
$(document).ready(function(){
    $("#toggleBtn").click(function(){
        $("#toggleText").toggle();
    });
});
 ```
![toggle text](img10.png)

### Joke API

I've effectively incorporated the jokeAPI into my website, allowing it to retrieve a fresh joke every minute and dynamically present it on the page.

Source code for Joke API:

```JS
<div id="response"></div>
    <script>
        $(document).ready(function () {
            $.get("https://v2.jokeapi.dev/joke/Programming?type=single", function (result) {
                console.log("From jokeAPI: " + JSON.stringify(result));
                $("#response").html("A programming joke of the day: " + encodeInput(result.joke));
            });
        });

        function encodeInput(input) {
            // You can add your own encoding logic here if needed
            return input;
        }
    </script>
```
![Joke API](img11.png)

### Weather API

I've successfully integrated the Weatherbit API into my website, enabling it to retrieve and display current weather information for Cincinnati.

```JS

<div>
                    <p id="weather"></p>
                </div>
                <script>
                    $(document).ready(function () {
                        const apiKey = 'c1d2b08a2c144aaea279ebd103d352f5';
                        const targetCity = 'Cincinnati';
                        const targetCountry = 'US';
                        const weatherUrl = `https://api.weatherbit.io/v2.0/current?&key=${apiKey}&city=${targetCity}&country=${targetCountry}`;

                        $.get(weatherUrl, function (response) {
                            const currentTemp = response.data[0].temp;
                            const condition = response.data[0].weather.description;
                            const displayInfo = `Current temperature and weather condition in ${targetCity}: ${currentTemp}°C, ${condition}`;
                            $('#weather').html(displayInfo);
                        });
                    });
                </script>
```

![weather API](img14.png)

### Javascript Cookies

I have implemented JavaScript cookies on my website to remember the client's visit. Now, it displays personalized messages based on whether the user is a first-time visitor or a returning user. For first-time visitors, the message is "Welcome to my homepage!", and for returning users, it shows "Welcome back! Your last visit was (last visit time and date)".

```JS

  <script>
    // Function to set a cookie with a specified name, value, and expiration days
    function setCookie(name, value, days) {
      var expires = "";
      if (days) {
        var date = new Date();
        date.setTime(date.getTime() + (days * 24 * 60 * 60 * 1000));
        expires = "; expires=" + date.toUTCString();
      }
      document.cookie = name + "=" + value + expires + "; path=/";
    }

    // Function to get the value of a cookie by name
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

    // Function to check if it's the first-time visit
    function checkFirstVisit() {
      var isFirstVisit = getCookie("firstVisit");
      if (!isFirstVisit) {
        // Display welcome message for the first-time visit
        alert("Welcome to my homepage!");
        // Set the cookie to remember the visit for 365 days
        setCookie("firstVisit", "true", 365);
      } else {
        // Display welcome back message for returning visitors
        var lastVisit = getCookie("lastVisit");
        alert("Welcome back! Your last visit was " + lastVisit);
      }
      // Set the cookie for the current visit
      setCookie("lastVisit", new Date(), 365);
    }

    // Call the function to check for the first-time visit
    checkFirstVisit();
  </script>

```
![First visit](img12.png)
![revisit cookies](img13.png)
















