---
title: 'Dom Manipunation'
layout: post
date: 2019-06-26 08:44
# image: /assets/images/markdown.jpg
headerImage: false
tag:
    - markdown
    - elements
star: true
category: blog
author: terence
description: Introduction of dom manipulation
---

## Outline

-   DOM defind and structure
-   Targeting DOM element
-   Changing elements' contents
-   Changing elements' styles

<br>
### DOM defind and structure

DOM represents document object moduel, document object is a property/node of the window object in the browser. The document object is a tree node structure, see the example belows:

-   document
    -   DOCTYPE
    -   HTML
        -   head
        -   body
            -   header
            -   ...
            -   footer

### Targeting DOM element

> Seleting by attribute's value

-   getElementById()
-   getElementsByClassName()
-   getElementsByName()
-   getElementsByTagName()
-   getElementsByTagNameNS()

```javascript
document.getElementById('hello');
```

<br>

> Selecting by CSS selectors

-   querySelectAll()

```javascript
document.querySelectAll(div[class="application-main "]) //by attribute and value

document.querySelectAll('#hello') //by id

document.querySelectAll('.pClass') //by class

document.querySelectAll('h1') //by tag
```

<br>

### Changing elements' contents

> Predefine: let el = document.getElementById('hello')

{%gist Tzhong16/baa4ba65e75079f29e39bc4298c56f94%}

-   innerText
-   innerHTML
-   outerText
-   outerHTML

`innerText` : get text contents of target element

`innerHTML` : get raw html contents within target element

`outerText` : similar to innterText, get text contents of target element, but if sign string value to this property will also overwrite the tags of taget element itself.

`outerHTML` : get raw html contents includes target element

### Changing elements' styles

> Predefine: let el = document.getElementById('hello')

`style` : change by style object

```javascript
el.style.backgound = 'black';
```

`cssText` : change multiple properties in one line

```javascript
el.cssText = 'backgound: black color: white font-size: 32px';
```

`getComputedStyle` : the computed style comes from browser predefind and CSS style sheet. This is different from the way of JavaScript change the style of element, JS only use the style attribute to change the style.

### Add Event to elements

Event is use to help people interate with the web content, such as mouse click, keyboard press. Two ways to do this, adding `event listener` or sign function to `event property`:

```html
<select name="animal">
    <option value="cat">Cat</option>
    <option value="dog">Dog</option>
    <option value="pig">Pig</option>
    <option value="duck">Duck</option>
</select>
```

1.  Event Listener
    When explore the select element property will see many events' properties such as onclick, on change, oncancel .... All these event properties under a namespace `on..`, when add event listener to a element, only use the word after on, like `click, cancel, change` :

`addEventListener` : add event listener on a element, we can add as many as we want.

```javascript
function callBackEvent(e) {
    console.log('I was clicked');
}

el.addEventListener('click', callBackEvent);
```

`removeEventListener` : remove event listener on a element

```javascript
el.removeEventListener('click', callBackEvent);
```

2. Event property

Element has many event properties like onclick, onblur, onfocus. We can sign a callback function to these properties and this is the common way.

```javascript
el.onclick = function(e) {
    console.log(e, 'on click');
}; // every call back function take event as a parameter
```

### Add Elements by JS

`createElement()` : create an element to document
`appendChild()` : append child element to body

```javascript
let el = document.createElement('div');

el.style.cssText = 'background: blue; width: 100px; height: 100px';
el.onclick = function() {
    alert('haha');
};

document.body.appendChild(el);
```

`insertBefore` :

```javascript
let el = document.createElement('div');

el.style.cssText = 'background: blue; width: 100px; height: 20px';
el.onclick = function() {
    alert('haha');
};
let elBlack = document.getElementById('black');

document.body.insertBefore(el, elBlack);
```
