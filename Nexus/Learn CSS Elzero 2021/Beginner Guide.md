CSS stands for Cascade Style Sheet

→ first let's create a basic html with a paragraph: 

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <p>This is a Paragrpah</p>
</body>
</html>
```

now in the `style.css` file: 

→ if we're targeting an element like the `<p>` we type:

```css
p {
	color: red;
}
```

→ if we're targeting a class like this: 

```html
<p class="para">This is Paragraph</p>
```

we type in the css: 

```css
.para {
	color: red;
}
```

→ we can target id (not recommended) by using the `#`

## Naming Best Practice

the best practice is to use the kebab case like this: 

nav-bar

## Display Block, Inline, Inline Block

Block

  - Block is the default option applied automatically \[you don't have to add css to apply it]
  - Take Full Width If No Width is defined
  - Adds Line Breaks
  - Respect Padding, Margin, Width, Height


  Inline

  - Do Not Respect Width, Height \[adding width or height won't make a difference]
  - Respect Padding And Margin \[ Just right + Left ]
  - Doesn't Add Line Break
  - Allow Elements Before And After It in The Same Line

  Inline-Block

  - a mix between inline and block
  - Allow Elements Before And After It in The Same Line \[just like inline]
  - Respect Padding, Margin, Width, Height \[just like block]
  - in other words it's a version of inline but respect margin, padding, width, and height. 

PS: the `div` element is a block element while the `span` element is inline by default. 

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>CSS</title>
    <link rel="stylesheet" href="css/master.css" />
  </head>
  <body>
    <div>Div => Block</div>
    <div>Div => Block</div>
    <div>Div => Block</div>

    <span>Span => Inline</span>
    <span>Span => Inline</span>
    <span>Span => Inline</span>
  </body>
</html>
```

```css
span {
  background-color: #EEE;
  display: inline-block;
}
```

## Display None vs Visibility Hidden

→ if the display is set to none that means the object won't be visible and it's used with javascript to hide or unhide elements based on certain scenarios. 

→ if the visibility is set to hidden that also makes that element not visible but the key difference between display none and visibility hidden is that when you set the element to display none the next element takes it's place in the webpage flow but when you set the element visibility to hidden it keeps it's place in the page flow but remains hidden. 

→ one of the use cases of the visibility is to create animation when you scroll to the element using a script called `wow.js` you can find it in the following link: 

https://wowjs.uk

## Grouping Multiple Selectors

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>CSS</title>
    <link rel="stylesheet" href="css/master.css" />
  </head>
  <body>
    <div class="one">One</div>
    <div class="two">Two</div>
    <div class="three">Three</div>
    <div class="four">Four</div>
    <p class="my-p">This Is P</p>
  </body>
</html>
```

```css
.one {
  border-bottom: 2px solid red;
  color: red;
}
.two {
  border-bottom: 2px solid green;
  color: green;
}
.three {
  border-bottom: 2px solid blue;
  color: blue;
}
.four {
  border-bottom: 2px solid black;
  color: black;
}
.one,
.two,
.three,
.four,
.my-p {
  padding: 15px;
  margin: 12px 0;
  background-color: #ededed;
}
```

## Nesting

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>CSS</title>
    <link rel="stylesheet" href="css/master.css" />
  </head>
  <body>
    <div>
      <h2>Title</h2>
      <p>Paragraph Inside Div</p>
      <p class="special">Paragraph Inside Div With Class</p>
    </div>
    <p class="special">Paragraph Outside Div</p>
  </body>
</html>
```

```css
div .special {
  color: red;
}
```

## Dimensions – Width And Height

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>CSS</title>
    <link rel="stylesheet" href="css/master.css" />
  </head>
  <body>
    <div>Osama Mohamed</div>
    <hr>
    <div>Osama Mohamed Ahmed</div>
    <hr>
    <div>Osama Mohamed Ahmed Sayed</div>
  </body>
</html>
```

```css
div {
  background-color: red;
  padding: 10px;
  display: inline-block;
  max-width: 400px;
}
```

**PRO TIP:** when you create a paragraph element `<p>` you can just type the word `lorem` and hit tab ⇥ and this will create a paragraph block for you. 

## Overflow – Overflow-X And Overflow-Y

- the default overflow value if it's not defined is visible (the overflow text will be visible beyond the element dimension)
- setting the overflow to scroll will show the x and y scrolling
- setting the overflow to auto will show the x and y scrolling only if the text is going beyond the div dimension.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>CSS</title>
    <link rel="stylesheet" href="css/master.css" />
  </head>
  <body>
    <div>
      Lorem ipsum dolor sit amet consectetur adipisicing elit.
      Inventore sit molestiae, corrupti at quae debitis dicta
      adipisci unde, nemo, veritatis error. Cupiditate,
      deserunt maiores assumenda ut quod voluptate adipisci repellat.
    </div>
  </body>
</html>
```

```css
div {
  width: 150px;
  height: 150px;
  background-color: #EEE;
  margin: 20px auto;
  border-radius: 6px;
  overflow: scroll;
}
```

## Inheritance

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>CSS</title>
    <link rel="stylesheet" href="css/master.css" />
  </head>
  <body>
    <div>
      <h3>Elzero Web School</h3>
      <p>Welcome To The Website</p>
    </div>
  </body>
</html>
```

```css
div {
  text-align: center;
  padding: 20px;
  background-color: #EEE;
  font-size: 20px;
  border: 2px solid blue;
}
div p {
  border: 2px solid;
  border-color: inherit;
  padding: inherit;
}
```

## Mouse Cursor

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>CSS</title>
    <link rel="stylesheet" href="css/master.css" />
  </head>
  <body>
    <a href="#">Google</a>
    <span>Test</span>
    <button>Click</button>
    <hr>
    <p>This Is P</p>
    <p>This Is P</p>
    <p>This Is P</p>
  </body>
</html>
```

```css
button {
  background: transparent;
  border: none;
  color: red;
  font-weight: bold;
  cursor: pointer;
}
```

## Position

1. **Static**: The default position. Elements appear in the normal document flow (where they would naturally fall on the page). No special positioning applied.

2. **Relative**: The element stays in the normal document flow, but you can move it slightly (using top, right, bottom, left) relative to where it would normally be.

3. **Absolute**: The element is removed from the normal document flow and positioned relative to the nearest positioned ancestor (an ancestor with a position other than static). If there’s no such ancestor, it positions itself relative to the `<html>` element.

4. **Fixed**: The element is removed from the normal document flow and positioned relative to the viewport, meaning it stays in the same place on the screen even when scrolling.

5. **Sticky**: The element acts like relative until you scroll past a certain point, then it “sticks” to that position on the viewport. It’s often used for things like sticky headers.

## Z-Index

Z-Index sets the stack order of an element along the z-axis (front-to-back). Higher z-index values bring elements to the front, while lower values push them behind other elements. It only works on positioned elements (relative, absolute, fixed, or sticky).

→ if the z-index value is set to -1 that means it's behind everything (like send to back in photoshop)

