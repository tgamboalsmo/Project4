PIZZA.HTML Site - Web Optimized Version
Optimized by: Tim Gamboa
Date: July 2015

Objective:  
==========
The purpose of this project was to take an existing mock pizza website with many performance 
problems, identify those problems and resolve them.

Goal and Measure:  
=================
For this site to be considered optimized, it has to meet several criteria. On the Google 
Page Speed Insights tool (https://developers.google.com/speed/pagespeed/insights/), a score 
of 90 or higher has to be achieved. From within Chrome Dev Tools, a frame rate of 60fps has 
to be achieved during scrolling and the resize pizzas time has to occur in less than 5ms.

General Application Usage and Functionality:
============================================
The mock pizza business is called Cam's Pizzeria. On load, you will see menu options at the
top of the screen and general information about the pizza products along with an image of
a pizzeria. In the background, there are floating pizzas in rows. They will animate left 
and right when scrolling is performed. When scrolling down, a random list of pizzas will
be displayed with random names and ingredients. At the top of the random pizzas will be a
slider. You will be able to adjust the size of the pizza(small, medium and large) by
sliding the button left or right. The pizzas will change in size respectively (not the
floating pizzas in the background.

Key Files:
==========
Javascript - main.js
CSS - Inline CSS and boostrap.min.css
HTML - pizza.html
Images - pizza.png and pizzeria.jpg


Performance Improvements:
=========================

main.js
-------
1 - document.addEventListener('DOMContentLoaded', function() - decreased the number of 
moving pizzas from 200 to 40 pizzas. No need to have that many since all 200 would never 
show up anyways.

2 - updatePositions() - moved document.body.scrollTop outside the forloop which decreased
the number of FSL initially.

3 - changePizzaSizes() - removed call to determineDX() and moved the switch inside
changePizzaSizes. Then adjusted the calculations to a percentage instead of pixels. Also
consolidated the querySelectorAll to just 1 call.

4 - //document.addEventListener('DOMContentLoaded', function() - change the function
associated to this listener into a normal function be called normall versus waiting for
content loaded. Renamed to loadMovingPizzas().

4 - loadMovingPizzas() and pizzaElementGenerator - was calling for the images/pizza.png 
for each pizza. I set a new global variable to load it once, then each pizza will call 
that variable in the FOR loop.

5 - FOR loop containing pizzasDiv.appendChild(pizzaElementGenerator(i)) - cut down the
number of pizzas from 100 to 30. 100 didn't seem practical or efficient. Users likely
would scroll past the first 30 before deciding they might want to use a filter, if
applicable.

6 - loadMovingPizzas() - moved the querySelector outside of the FOR loop to only allow 1 
query instead of 1 for each loop.

7 - updatePositions() - set up a value to be passed from calling function to identify if
updatePositions() is being called from the initial load or scroll. This is to resolve
the FSL that was occurring during the initial load using the scrollTop method. The initial
load doesn't really need scrollTop, so set it to 0. When the scroll listener calls this
function, it will use scrollTop as normal.

8 - for loop that calls pizzaElementGenerator() - moved the getElementbyID above the for 
loop.

9 - updatePositions() - removed i % 5

10 - querySelectxxxx - removed querySelector's and replaced with getElementsbyClassName,
ID, etc

11 - moved definition of variable to the outside of for loops
 
12 - minified main.js

13 - deferred the creation of the random pizzas until DOMContentLoaded as the pizzas are
below the fold on initial load of the page.

CSS
---------
1 - .mover and .randomPizzaContainer - added 'will-change: transform;' to this class to 
get the moving pizzas to their own layer.

2 - Inlined CSS into index.html since style.css was not very big.

3 - minified bootstrap.min.css and moved it to the bottom of the body in pizza.html

pizza.html
----------
1 - <meta name=viewport content="width=device-width, initial-scale=1"> - added this to
header for mobile devices.

2 - Removed the 2 random pizzas hard coded into the html and deferred their creation to
the pizzagenerator in main.js

3 - javascript tag - async'd and moved to the header.

4 - Removed inline css attributes for 2 h2 elements (Locations and Our Pizzas) and 
replaced with class="centered"

5 - minified pizza.html


images
------
1 - pizzeria.jpg - compressed 17kb from 2mb. It's a smaller image, but it didn't need
to be large for this website.

2 - pizza.png - compressed down to 18kb.

