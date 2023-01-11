# Assignment-6
Explain event bubbling and capturing with an example.

Event bubbling and capturing are two ways of event propagation in the HTML DOM API, when an event occurs in an element inside another element, and both elements have registered a handle for that event. The event propagation mode determines in which order the elements receive the event. 
 
## Event Bubbling
 Event Bubbling is a concept in the DOM (Document Object Model). It happens when an element receives an event, and that event bubbles up (or you can say is transmitted or propagated) to its parent and ancestor elements in the DOM tree until it gets to the root element.

 Example of event bubbling:
 
 HTML:
 ```html
 <body>
  <div>
    <span>
      <button>Click Me!</button>
    </span>
  </div>
</body>
```
CSS:
```css
body {
  padding: 20px;
  background-color: pink;
}

div {
  padding: 20px;
  background-color: green;
  width: max-content;
}

span {
  display: block;
  padding: 20px;
  background-color: blue;
}
```

Javascript:
```js
const body = document.getElementsByTagName("body")[0]
const div = document.getElementsByTagName("div")[0]
const span = document.getElementsByTagName("span")[0]
const button = document.getElementsByTagName("button")[0]

body.addEventListener('click', () => {
  console.log("body was clicked")
})

div.addEventListener('click', () => {
  console.log("div was clicked")
})

span.addEventListener('click', () => {
  console.log("span was clicked")
})

button.addEventListener('click', () => {
  console.log("button was clicked")
})
```
Here, we've selected the body, div, span, and button elements from the DOM. Then we added the click event listeners to each of them and a handler function that logs "body was clicked", "div was clicked", "span was clicked", and "button was clicked", respectively.  
  
What happens on the console when you click on the pink background (which is the body) is:  
```
body was clicked
```  
When you click on the green background (which is the div), the console shows:  
```
div was clicked
body was clicked
```  
The "click" event on the body element is triggered even though the div element was the target element clicked because the "click" event bubbled from the div to the body.

When you click on the blue background (which is the span), the console shows:  
```
span was clicked
div was clicked
body was clicked
```  
And, lastly, when you click on the button, the console shows:  
```
button was clicked
span was clicked
div was clicked
body was clicked
```  
## Event Capturing
Event capturing is one of two ways to do event propagation in the HTML DOM. In event capturing, an event propagates from the outermost element to the target element. It is the opposite of event bubbling, where events propagate outwards from the target to the outer elements. Events trickle down in event capturing.

Example of Event Capturing:
The HTML and CSS part is same as above program and the Javascript is given below:
```js
        const body = document.getElementsByTagName("body")[0]
        const div = document.getElementsByTagName("div")[0]
        const span = document.getElementsByTagName("span")[0]
        const button = document.getElementsByTagName("button")[0]

        body.addEventListener('click', () => {
            console.log("body was clicked")
        }, true)

        div.addEventListener('click', () => {
            console.log("div was clicked")
        }, true)

        span.addEventListener('click', () => {
            console.log("span was clicked")
        }, true)

        button.addEventListener('click', () => {
            console.log("button was clicked")
        })
```
This program works same as the above program but the only difference is when you click the child element, it first logs its ancestor elements followed by its parent element and finally the element itself.