# GimmeKitteh

**GimmeKitteh** is a simple API request call to [thecatapi.com](thecatapi.com). It was one of my first foray in working with API requests.

Have a look at the project over at https://jellyfishfingers.github.io/gimmekitteh/

## What you need to know
HTML, CSS, jQuery, JSON

## Installation
Download / Clone the project into your computer, and open the index.html in your favourite text editor. 

## How this works?

This API request (https://api.thecatapi.com/v1/images/search?mime_types=gif) returns the following JSON String. 

```
    [
        {
            "breeds":[],
            "id":"4j7",
            "url":"https://cdn2.thecatapi.com/images/4j7.gif",
            "width":209,
            "height":199
        }
    ]
```
Each API request returns a random _single_ cat image. The **_url_** in the JSON results is the link to the cat image on the world wide web! The JSON results also contains other information, such as the _width_ and the _height_ of the image, which you can use if required..

I've also filtered down the search results to only return image type that are _animated gifs_. Why? Because animated gifs are more more hilarious. This is included as part of the parameters I've provided in the API Request under _mime_types=gif_.

The jQuery function I've built will make an API request and appends my HTML information with the API results.

```
    function callKitty() {
        $.getJSON("https://api.thecatapi.com/v1/images/search?mime_types=gif",function(data){
            var caturl = data[0].url;   //Gets only the URL portion of the JSON data.
            $(".kittypicdiv").html("<img src='" + caturl + "' width='100%'>"); // Appends my part of the HTML Document with the cat URL.
        });
    }
```
