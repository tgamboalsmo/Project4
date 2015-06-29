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

4 - document.addEventListener('DOMContentLoaded', function() and 
pizzaElementGenerator - was calling for the images/pizza.png for each pizza. I set a new 
global variable to load it once, then each pizza will call that variable in the FOR loop.

5 - FOR loop containing pizzasDiv.appendChild(pizzaElementGenerator(i)) - cut down the
number of pizzas from 100 to 30. 100 didn't seem practical or efficient. Users likely
would scroll past the first 30 before deciding they might want to use a filter, if
applicable.

6 - document.addEventListener('DOMContentLoaded', function() - moved the querySelector
outside of the FOR loop to only allow 1 query instead of 1 for each loop.


style.css
---------
1 - .mover - added 'will-change: transform;' to this class to get the moving pizzas to
their own layer.

2 - Inlined CSS into index.html.

images
------
1 - Reduced Pizzeria.jpg from 2MB to 413KB.