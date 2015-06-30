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

9 - height and width for loadMovingPizzas and pizzaElementGenerator - moved the CSS to the 
inline CSS.

10 - updatePositions() - added translateX and Z.

11 - pizzaElementGenerator() and loadMovingPizzas() - removed height and width styles from
those functions and added them to the inline CSS.


style.css
---------
1 - .mover and .randomPizzaContainer - added 'will-change: transform;' to this class to 
get the moving pizzas to their own layer.

2 - Inlined CSS into index.html since style.css was not very big.

pizza.html
----------
1 - <meta name=viewport content="width=device-width, initial-scale=1"> - added this to
header for mobile devices.

2 - Removed the 2 random pizzas hard coded into the html and deferred their creation to
the pizzagenerator in main.js

3 - javascript tag - async'd and moved to the header.

4 - Removed inline css attributes for 2 h2 elements (Locations and Our Pizzas) and 
replaced with class="centered"


images
------
1 - pizzeria.jpg - download new 640x480 version and compressed down to 95kb from 2mb.

2 - pizza.png - compressed down to 18kb.

