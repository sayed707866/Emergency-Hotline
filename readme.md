##  What is the difference between getElementById, getElementsByClassName, and querySelector / querySelectorAll?
Ans:
1. getElementById("idName")
It selects one element with the given id. Then return a single element object.
Example:
document.getElementById("mobile-number");
//it finds the element with id=" mobile-number "
All the IDs are unique.
2. getElementsByClassName("className");
It selects all elements with the given class name. It returns an HTMLCollection, which is array-like but not a real array.
Example:
document.getElementsByClassName("form");
//it finds all elements with class="form"
3. querySelector("cssSelector")
What it does: Selects the first element that matches a CSS selector.It returns a single element.
document.querySelector(".item");
//it finds the first element with class="item".
Even if we have multiple element with the same name, it will only return the very first element it finds.
4. querySelectorAll("cssSelector")
What it does: Selects all elements that match a CSS selector.It returns a NodeList, which is similar to an array and supports forEach.
Example:
document.querySelectorAll(".laptop");
//it finds all elements with class="laptop".


## How do you create and insert a new element into the DOM?
Ans:
Steps to create and insert a new element into the DOM:
We can create element by using  document.createElement( ) 
Then we can add the element into the DOM by using textContent, className, etc. 
Then we can insert into DOM, by using appendChild()
Example:
let newHeading = document.createElement("h");
// creates new heading(h) element  
newHeading.textContent = "Foods";  
// adds the new heading in the DOM
document.body.appendChild(newHeading);
// inserts the new heading in the DOM
Output: A new <h> with "Foods" appears in the body. 
## What is Event Bubbling and how does it work?
Ans:
Event bubbling in JavaScript means that when an event happens on a child element, it runs first on that element and then moves up through its parent elements.
How it works:
Event Trigger:  
When an event happens on an element, like a click on a button, that specific target element handles the event first. 
Propagation Upwards:  
After the target element processes the event, it moves to its immediate parent element. If there is an event listener attached to this parent element for the same type of event, that listener will also activate.
Continued Bubbling:  
This keeps going, with the event moving to the grandparent, great-grandparent, and all other ancestors in the DOM tree, triggering any related event listeners along the way.
Reaching the Root:  
Bubbling usually goes on until the event reaches the document or window object, unless it is stopped intentionally.
Example:
JavaScript:  
document.getElementById("parent").addEventListener("click",  function(){  
  console.log("Parent clicked");  
});  
document.getElementById("child").addEventListener("click", function(){  
  console.log("Child clicked");  
});  
When the button is clicked, the output will be:
Child clicked  
Parent clicked  
This shows the event bubbling from child to parent.

## What is Event Delegation in JavaScript? Why is it useful?
Ans:
Event Delegation in JavaScript is a technique where you attach a single event listener to a parent element. This listener manages events for its child elements by using event bubbling.
Usefulness:
1.It improves performance by reducing the number of listeners.
2.It works even if new child elements are added dynamically.
3.It keeps the code simple and easy to manage.
Example:
document.querySelector("ul").addEventListener("click", (e) => {
    if (e.target.tagName === "LI") {
        console.log("Clicked:", e.target.textContent);
    }
});

In this example, only one listener on <ul> handles clicks for all <li> elements.

## What is the difference between preventDefault() and stopPropagation() methods?
Ans:
preventDefault() stops the browser from doing its usual action for an event, such as stopping form submission.
On the other hand,  stopPropagation() prevents the event from moving up to parent elements in the DOM tree.

Example:

document.querySelector("a").addEventListener("click", (e) => {
    e.preventDefault();   // stops link navigation
    e.stopPropagation();  // prevents bubbling to parent
});

In this example, clicking the link won’t open the URL (preventDefault) and the event won’t reach its parent (stopPropagation).
