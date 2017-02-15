# Notes, learning, snippets

## Events propagation by bubbling (default) or capture: http://codepen.io/PiotrBerebecki/pen/rjRVeQ

```html
<div>
  <p>JS Fun</p>
</div>
```

```javascript
const divDOM = document.querySelector('div');
const pDOM = document.querySelector('p');

divDOM.addEventListener('click', log, {
  capture: false,
  once: false
});
// false is default 3rd argument (capture)
// change it to true to capture parent first
// if `once` is set to true the handler will unbind 
// itself after first event (no need to use
// remove event listener)

pDOM.addEventListener('click', log);

function log(e) {
  // console.log('target', e.target); // innermost first
  console.log('this', this); // always the object where event listenere was added
  // e.stopPropagation(); // stops propagation after first event
}

// 'this' is always the element that event listener was set on
// 'e.target' the actual element that was clicked on

// adding true as the third argument to event listener will change the event propagation from bubbling (default false) to capturing. This means that the events on parents will be captured first.
```
