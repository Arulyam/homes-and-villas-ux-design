# Marriott Bonvoy Hotels and Villas
This project was made with the assistance of resources provided by the Global Career Accelerator.

## Contents

- Research Summary
- Code Introduction
- Provided Code
- Additional Code

## Research Summary
### Understand Your Market
<hr/>

#### **Provide links to the 3 websites you explored**
1. https://www.airbnb.com/
2. https://www.vrbo.com/
3. https://www.wimdu.com/

#### **Briefly explain why these websites are a relevant comparison** 
These websites are a relevant comparison to our product, Homes & Villas by Marriott Bonvoy, as they are primarily focused and advertised on selling whole-home rentals. These whole-home rentals are presented as popular cities, experiences, or vacation sites where the location of one's stay matters. This is significant as our client's company aims to satisfy these exact needs of their customers. 

#### **List at least 10 product features**
- a user can search by location, dates, and guests immediately when entering the website
- a user can look at suggested popular cities/locations immediately when entering the website
- a user can filter a particular search after the initial search
- a user can quickly save locations they like in a list/trip board
- a user can view their upcoming trips in their account page
- a user can browse through cards based on filterations showing the price, reviews, and image immediately
- a user can select cards to view more information, get contact info, and book the rental
- a user can share the rental through many media platforms
- a user can explore the location of potential rentals on a map
- a user can quickly change region/language in navbar to allow site to better accomidate them


### Understand Your Users
<hr/>

#### **Write a short paragraph (50-100 words) describing the themes that emerged from the user research**
The user research suggests that the majority of our clinet's users have a good idea for the type of location they do or don't want, but do not have a destination in mind. Additionally, a large chunk of our clinet's users are looking for a location that they can relate to or inspires them to take that journey which varies from clinet to client. Many of Marriott Bonvoy members found that when the map or page is cluttered with too many options, the experience of exploring becomes daunting or tedious. These themes and futher research should improve the website to displaying types of getaways and inspirational material.

### Define and Prototype
<hr/>

#### **Paste a link to your prototype here**
*Don't forget to include a comment if you attempted any of the LevelUps, so that your grader knows to review your work and award the extra credit!* 
> **🗒️ NOTE:** Make sure you share your prototype file so that "anyone with the link" can view it. If we're unable to access your file, we'll be unable to give you credit.

Here is the link to the prototype using Google Slides. Make sure to view the slideshow "starting form the beginning" to skip instruction slides:
https://docs.google.com/presentation/d/1S8MzeEsscAACsY726sHIbnieGKq7tZ2_7hQ186QQCFo/edit?usp=sharing

*Additional*
- The high fidelity prototype uses graphics that will accurate to the website and supports high interactivity such as many buttons and scrolling. Only negative of prototype is not supporting beach and mountain buttons, but this oversight is permitted in task instructions. 
- The prototype provides an additional feature of closing the modal without having to choose a type of location. This is ideal for over 25% of our clinet's users that have an exact location in mind and would rather search in the search box.

## Code Introduction 
With your product research finished and your priorities established, it's time to write some code. 

When the page loads, users will be greeted with a popup modal that asks them where they want to go - "city", "beach", or "mountains". When the user selects an option, the modal will disappear and the page should generate a list of recommended destinations. Your task is to write the logic that will select and render recommendations to the page as cards in the "Recommendations" section and text in the "Destinations" dropdown. 

There are plenty of comments and scaffolding to help you get the job done in `script.js`. Keep in mind that the tasks in the Deliverable section build upon each other so **you should complete each task in order!**

> **🗒 Note:** The only file you'll need to code in to complete this project is `script.js`.

## Provided Code

**`PLACES`** - This is an array that lives in the `places.js` file. Go ahead and examine it to see what each place object looks like. Each place has properties that you'll use for filtering.

**`centerPlaceOnMap(placeName)`** - This function works with the Open Layers API to pan the map to a selected location. 

## Additional Code

### Function 1 - **`filterPlacesByType(typePreference)`**

| Parameter        | Type   | Example Argument |
| ---------------- | ------ | ---------------- |
| `typePreference` | String | `"beach"`        |

This function returns a filtered array of places based off the user's type preference.

Filters the `PLACES` array by comparing the `type` of each place with the argument supplied to the `typePreference` parameter. The function returns a new array of filtered places.

<hr>

### Function 2 - **`createCard(place)`**

| Parameter   | Type   | Example Argument |
| ----------- | ------ | ---------------- |
| `place`     | Object | `{name: "Algarve", location: "Portugal", long: -7.93044, lat: 37.019356, img: "assets/images/popular-destinations/algarve.jpg", type: "beach"}`|

This function accepts a single place object as an argument. It creates a Bootstrap column containing a card for the specified `place` using DOM manipulation and return it. 

To make sure the card is styled properly and integrates with the provided Open Layers API logic, the column has the same structure as the HTML below. Take special note of the card's `onclick` attribute. It calls the included `centerPlaceOnMap` function that pans the map to the selected location. It passes the name of the place whose card you're creating. 


```html 
<div class="col">
  <div class="card h-100" onclick="centerPlaceOnMap(place.name)">
    <img src="..." class="card-img-top h-100" alt="...">
    <div class="card-body">
      <h5 class="card-title">place.name</h5>
      <p class="card-text">place.location</p>
    </div>
  </div>
</div>
```

To test the logic, call the function from the console and pass in an object from `PLACES`. The column and card elements will be displayed in the console.

> **Note:** This was easily accomplished with template literals. To learn more about creating HTML elements with template literals, check out [this awesome article from Wes Bos.](https://wesbos.com/template-strings-html)

<hr>

### Function 3 - **`populateRecommendationCards(filteredPlaces)`**

| Parameter        | Type  | Example Argument |
| ---------------- | ----- | -----------------|
| `filteredPlaces` | Array | `[{name: "Algarve", location: "Portugal", long: -7.93044, lat: 37.019356, img: "assets/images/popular-destinations/algarve.jpg", type: "beach"}, {name: "Bali", location: "Indonesia", long: 115.188919, lat: -8.409518, img: "assets/images/popular-destinations/bali.jpg", type: "beach", }, ...]` |

This function accepts a filtered array of place objects as an argument (e.g. all places with the type "beach"). To start, the DOM element with the id "recommendations" is cleared out. 

Next, `filteredPlaces` is looped through and the `createCard` function wrote in task 2 to create DOM elements for each place object is called.

Finally, each created card is apeended to the "recommendations" div to populate the "Recommended for You" section.

<hr>

### Function 4 - **`findPlaceByName(placeName)`**

| Parameter   | Type   | Example Argument |
| ----------- | ------ | ---------------- |
| `placeName` | String | `"Bali"`         |

This function finds an object in `PLACES` where the object's `name` property matches the argument passed to the `placeName` parameter. It's used to pin our place on the interactive map and fly to it when clicked from the dropdown menu or the "Recommended for You" section.

To do this, the array of `PLACES` is looped through and the place object where the `name` property is the same as `placeName` is utilized. The function should return that place object.
