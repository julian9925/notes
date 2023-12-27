
## event bubbleing and capturing exection order

Below is the html example

```html
<body>
	<ul onclick="alert('ul')" id="myList">
		<li onclick="alert('li')">Item 1</li>
		<li>Item 2</li>
		<li>Item 3</li>
	</ul>
</body>

<script>
  const myList = document.getElementsByTagName('ul')[0];

  myList.addEventListener('click', function(event) {
     const target = event.target;

     if (target.tagName === 'LI') {
        let backgroundColor = target.style.backgroundColor;
        target.style.backgroundColor = backgroundColor === 'yellow' ? '' : 'yellow';
     }
  });
</script>
```

What is the order of execution of the event handlers?

This is event bubbling. The order of execution is
1. li -> alert('li')
2. ul -> alert('ul')

This is event capturing. Listenter is binded to the ul element.
3. ul -> event handler change the background color of the li element

- Event Capturing (or "Capturing Phase"): This phase is "top-down". It starts from the outermost element (typically the document object or the window object) and trickles down to the target element where the event actually occurred.

- Event Bubbling: This phase is "bottom-up". After the event has reached its target in the capturing phase, it starts to bubble up from the target element to the outermost element.

## stopPropagation and preventDefault


`stopPropagation` and `preventDefault` are both methods available on the event object in the DOM, but they serve different purposes. Here's a breakdown of their differences:

### 1. `stopPropagation`:

- **Purpose**: To prevent the event from propagating (or traveling) through either the capturing or bubbling phases.
  
- **Effect**:
  - In a bubbling phase: If an event handler on a child element calls `stopPropagation`, parent elements will not be notified of the event.
  - In a capturing phase: If an event handler on a parent element calls `stopPropagation`, child elements will not receive that event during the capturing phase.
  
- **Common Use Cases**: 
  - When you want to ensure that only a specific element handles the event and you don't want parent (or child, in capturing mode) elements to know about it.
  - When nested components might have conflicting event handlers, and you want to ensure only one of them is executed.

### 2. `preventDefault`:

- **Purpose**: To prevent the browser's default behavior associated with the event.
  
- **Effect**: Stops the default action associated with the event from occurring. For example:
  - Clicking a link: By default, it navigates to the link's href. Using `preventDefault` will stop the navigation.
  - Submitting a form: By default, it sends the form data to the server. Using `preventDefault` will stop the form submission.
  
- **Common Use Cases**: 
  - When you want to replace the default behavior with custom behavior. For instance, you might want to use AJAX to submit a form instead of the regular form submission.
  - Preventing any unwanted default actions while still allowing the event to propagate through the DOM.

### In summary:

- `stopPropagation` is about controlling the flow of the event through the DOM tree.
- `preventDefault` is about controlling the browser's default behavior for the event.

They can be used independently or together, depending on the situation. For example, in a form's submit event handler, you might want to validate the form data using JavaScript and, if validation fails, both prevent the form from submitting (`preventDefault()`) and also stop any other submit handlers from being notified (`stopPropagation()`).