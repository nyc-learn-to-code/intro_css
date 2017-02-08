# Intro CSS
## Basics

<!-- toc -->

- [Objectives](#objectives)
- [Vocabulary](#vocabulary)
- [CSS Basics](#css-basics)
  * [Simple Selectors](#simple-selectors)
    + [Questions](#questions)
  * [Simple Declarations](#simple-declarations)
- [Adding CSS](#adding-css)
  * [Internal Style](#internal-style)
  * [External CSS](#external-css)
- [The Box Model](#the-box-model)
  * [Width/Height](#widthheight)
    + [Percent](#percent)
    + [Pixel](#pixel)
      - [Max-Height/Width](#max-heightwidth)
  * [Height Percents](#height-percents)
  * [Margins](#margins)
    + [Horizontal Centering](#horizontal-centering)
  * [Border](#border)
  * [Padding](#padding)
  * [Zeroing](#zeroing)
  * [Exercises](#exercises)
- [Positioning](#positioning)
  * [Static (default](#static-default)
  * [Relative](#relative)
  * [Absolute](#absolute)
  * [Fixed](#fixed)
  * [Exercises](#exercises-1)
- [Cascade](#cascade)
  * [Multiple Classes](#multiple-classes)
- [Media Queries](#media-queries)
- [Import Google Fonts](#import-google-fonts)

<!-- tocstop -->

## Objectives

| Objectives |
| :--- |
| Describe and play with CSS rules and selectors. |
| Discuss and utilize introductory concepts for the box model. |
| Discuss and utilize some of the import/media queries. |

## Vocabulary

* **Tag**: The HTML markup representing the start or end of part of a document.

	* The `head` tag is used to denote the start/end of the meta-data of the document: `<head>` and `</head>`.
	* A `body` tag is used to denote the start/end of the content of a document: `<body>` and `</body>`.
* **Tag Attribute** or **Attribute**: a key and value pair provided on a starting **tag** to extend its definition with meta-data.
	* A common attribute added to a starting `tag` is `class` used to help clarify the semantic purpose of a tag.
		* Help describe the purpose of a paragraph:
			```html
				<p class="comment">Hello World</p>
			```
* **Element**: the start and end tags with the content between them make up an entire element.

	```html
		<div class="quote">Hello world</div>
	```		

* **DOM**: All elements defined in HTML are represented as objects in memory with a collection of attributes and behavior that are initially nested according to the provided HTML file and rooted in a single document object that is drawn on the page. The document can define links to CSS and JS that in utilize the document to select and define properties on various elements that affect appearance or behavior of elements in the HTML. Effectively, the DOM is the current state of the document elements after CSS and JS changes have been applied.
  * Example: Go to the Chrome developer console

    ```javascript
    document.querySelector('div#mainContent').style.background = "red";
    ```


## CSS Basics

Let's add a bit of style to our HTML. Let say we have something like the following:

```html
<!DOCTYPE html>
<html>
	<head>
		<title>Example</title>
	</head>
	<body>
		<p class="greeting">Hello!</p>
		<p class="message">Use the power of CSS.</p>
		<p class="urgent">Color me red.</p>
	</body>
</html>
```

Let's say we have a plan for the paragraphs in the above HTML.

* Make the `greeting` paragraph **bold** with text **twice as large as the other content**.
* Make the `message` have a **gray background** with **white** colored text.
* Make the `urgent` have a red border and width and height of `300px`.

CSS styling is a collection of rules we define using a **selector** and a **block of declarations**. Each **declaration** is a **property** and **value** defined for a the selected elements. Using CSS Rules we can accomplish the above tasks.

### Simple Selectors

A simple selector is just a **tag** name and **class** or **id** that identifies certain elements on a page.

```html
<p class="comment">Pizza is awesome!</p>
```

This can be selected using `p`, the tag name, and `.comment`, a dot prefix means it's a class attribute.

```css
p.comment {
}
```

If you are selecting a specific element by an `id` attribute then you prefix using a `#`.

```html
<div id="blog-errors">
	<p>Missing title.</p>
	<p>Post body cannot be empty.</p>
</div>
```

To select the errors we would using following selector.

```css
div#blog-errors {
}
```

#### Questions

* How do you select the following:

	```html
		<section class="blog-content"></section>
	```
* How do you select the following:

	```html
		<p id="blog-tags">styling, css, declarations, css-rules</p>
	```
### Simple Declarations

Now that we know how to use simple selectors we add simple declarations to change the properties of the selected elements.

```html
<!DOCTYPE html>
<html>
	<head>
		<title>Example</title>
	</head>
	<body>
		<p class="greeting">Hello!</p>
		<p class="message">Use the power of CSS.</p>
		<p class="urgent">Color me red.</p>
	</body>
</html>
```

Recall that we want to make the following changes:

* Make the `greeting` paragraph **bold** with text **twice as large as the other content**.
* Make the `message` have a **gray background** with **white** colored text.
* Make the `urgent` have a red border and width and height of `300px`.

We can start by adding selectors for the above elements:

```css
p.greeting {
}

p.message {
}

p.urgent {
}
```

Let's add declarations for the `greeting` that makes it bold and twice and large.

```css
p.greeting {
	font-weight: bold;
	font-size: 200%;
}
```

The `font-size` and `font-weight` are both common `font` related properties that you might find yourself changing.

Let's change the message to have a gray background and white colored text.

```css
p.messsage {
	background-color: gray;
	color: white;
}
```  

When it comes to coloring you'll usually be changing the background or font color.

Let's change the `urgent` paragraph to have a width and height of `300px` with a red border.

```css
p.urgent {
	border-style: solid;
	border-width: 1px;
	border-color: red;
	width: 300px;
	height: 300px;
}
```

This is a good example of how the `border` can be defined. However, we can actually be more brief with our definition of the border.

```css
p.urgent {
	border: solid 1px red;
	width: 300px;
	height: 300px;
}
```

We defined have the following CSS rules.

```css
p.greeting {
	font-weight: bold;
	font-size: 200%;
}

p.messsage {
	background-color: gray;
	color: white;
}

p.urgent {
	border: solid 1px red;
	width: 300px;
	height: 300px;
}
```

## Adding CSS

You can add your CSS rules in on of two main ways. You can add **internal** CSS rules using `style` tags or you can an **external** stylesheet using a `link` tag.

### Internal Style

```html
<head>
	<style>
		p.greeting {
			font-weight: bold;
			font-size: 200%;
		}

		p.messsage {
			background-color: gray;
			color: white;
		}

		p.urgent {
			border: solid 1px red;
			width: 300px;
			height: 300px;
		}
	</style>
</head>
...
```

### External CSS

`your_style.css`

```css
p.greeting {
	font-weight: bold;
	font-size: 200%;
}

p.messsage {
	background-color: gray;
	color: white;
}

p.urgent {
	border: solid 1px red;
	width: 300px;
	height: 300px;
}
```

Add the external stylesheet link in your `head`.

```html
<head>
	<link href="your_style.css" rel="stylesheet">
</head>
```

## The Box Model

The box model is classic way of handling spacing for elements using CSS. It has it's quirks, but we can quickly get a handle on them and make beautiful content.

### Width/Height

Before talking about `margins`, `borders`, and `padding` it will be important to establish some sense of how to set the height and width of an element. The height and width control the content area height/width, so after we learn more about `borders`, `margins`, and `padding` you'll need to factor those widths in make sure you're effective box width/height is appropriate.

#### Percent

Using percent `%` is a very flexible way of sizing boxes. You'll often be required to use `%` instead of specific values, because of their benefit in responsive designs.

The `%` is relative to the size of the element against which it is contained/positioned. There is more to come on positioning later.

If you just go about using percents it might not work for your `height`. This is because the document needs a specified height, and if it's not explicitly given one then it will be `0`. Any percent of `0` is `0`.

**Bad Height**

```css
.box {
  height: 50%;
  background-color: blue;
}
```

[Live Example](https://jsbin.com/jayibiziqe/edit?html,css,output)

**Proper Height**

```css
/*
  Add an html/body height first
*/
html, body {
  height: 100%
}

.box {
  height: 50%;
  background-color: blue;
}
```

[Live Example](https://jsbin.com/ruxixowayi/1/edit?html,css,output)

#### Pixel

A more explicit way to measure a box is in pixel widths. You may have a series of panels you want fixed to have dimensions (fine if it's in a responsive container).

```
.panel {
  display: inline-block;
  width: 100px;
  height: 100px;
  background-color: blue;
}
```

[Live Example](https://jsbin.com/mewomanona/1/edit?html,css,output)

##### Max-Height/Width

Sometimes you might only care about the max height of an element. This gives you the ability to set a limit on it's `height: auto` (the default). If you're using these properties it's typical to utilize a `overflow` too.

**Growing Vertically**

```css
.panel {
  max-height: 100px;
  width: 100px;
  background-color: blue;
}
```

[Live Example](https://jsbin.com/qosuturali/1/edit?html,css,output)

Note how the edge of the box stopped at the specified height, but the content visibly overflowed.

**Growing Vertically \w Overflow**

```css
.panel {
  max-height: 100px;
  width: 100px;
  background-color: blue;
  overflow-y: scroll;
}
```

[Live Example](https://jsbin.com/befapisome/1/edit?html,css,output)

### Height Percents

Using a percent for the height of an element can be troublesome; the height of an element defaults to `height: auto`.  Auto height scales with the content of the text in the box.

**Containing element has a specified height**

```css
html, body {
  height: 100%;
}

.box {
  background-color: yellow;
  height: 50%;
}
```

Here we have given the containing document a height so a box directly inside the body will have a the expected height of `50%`.

[Live Example](https://jsbin.com/xahedejita/edit?html,css,output)

**Containing element does not have a specified height**

Given the above CSS, if we now place the box in a `div` that doesn't have a specified height the `.box` will revert back to `height: auto`.

```html
<body>
  <div>
    <div class="box">
      Hello
    </div>
  </div>
</body>
```

This is because the `div` has `height: auto` and any percent of `height: auto` is computed to `height: auto`.

[Live Example](https://jsbin.com/naxivakido/1/edit?html,css,output)

You'll have trouble with height and vertical sizing/positioning in CSS, but with more experience you'll be able to tackle these problems for particular tasks.


**Resources**

[Aspect Ratios](http://www.mademyday.de/css-height-equals-width-with-pure-css.html)


### Margins

Are vertical and horizontal space added to the outside of an elements border. It gives visual separation from other blocks positioned next to it.

```css
.panel {
  background-color: yellow;
  height: 100px;
  width: 100px;
  margin: 10px;
}
```

The `margin: 10px` puts a ten pixel space around all four sides of the panel.

You can separately set the `left`, `right`, `top`, and `bottom` properties of the margin using the following patterns.

```css
.panel {
  /* Apply to all four sides */
  margin: 10px;

  /* vertical | horizontal */
  margin: 10px 20px;

  /* top | horizontal | bottom */
  margin: 10px auto 40px;

  /* top | right | bottom | left */
  margin: 2px 1px 0 auto;
}
```

The `auto` margin will just add the default margin for the element. Browsers have different defaults built in for various elements: `h1`, `div`, etc.

> Note: **horizontal* refers to `left` and `right`.  **Vertical** refers to `top` and `bottom`.


#### Horizontal Centering

A quick way to horizontally center an element is to set the `left` and `right` margins to `auto` size.

```css
.panel {
  margin: 0 auto;
}
```

### Border

The border of an element is the edge of the element, between the margins and padding.

```css
.panel {
  /* style | width | color */
  border: solid 1px blue;
}
```

[Live Example](https://jsbin.com/riburokewo/edit?html,css,output)

Other styles include `dashed`, `dotted`, `groove`, `inset`, and `outset`.

### Padding

Padding follows the same rules as the margin except it's key is `padding`. It controls the amount of space between the content area and the border.

![Live Example](https://jsbin.com/tisugudopo/edit?html,css,output)

### Zeroing

We've thrown in it in a few times already. But when you want to set a property to zero you can just say `0` and don't have to specify the units as `%` or `px`.

### Exercises

* In JS Bin create an element with class `big-banner` that takes up the full width of the page and is 500 pixels high. Give it a background color of your choice. Put a greeting inside your `.big-banner` element.
* Create an element with class `content`. Give it a width of `800px`, center it, and give it 20 pixels of horizontal padding and 50 pixels of vertical padding.
* Add an `h2` in your `content` element. Give it some fake text and a solid black bottom border 10 pixels wide.
* Add two of the following paragraphs to your `content` element. Give each paragraph a bottom margin of 20 pixels.

  ```
    <p>
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin in dictum nisi, at placerat massa. Proin lacinia consequat nulla at fermentum. Quisque at augue nec lectus tincidunt suscipit. Suspendisse sodales est nulla, a tristique libero vehicula ac. Aliquam nec felis sollicitudin felis viverra varius. Vivamus tincidunt, metus at maximus faucibus, velit nisl tempus libero, quis feugiat augue nisi nec ex. Nullam mattis ante efficitur nisl venenatis ultricies. Aenean venenatis, ex vel elementum sollicitudin, magna nisl rhoncus diam, eget viverra arcu sem sed nunc. Aenean nec ante ultricies nisl tempor condimentum. Vestibulum et justo quam. Nunc lacinia auctor neque, vitae porta metus sollicitudin id. In hac habitasse platea dictumst. Suspendisse eget velit elit.
    </p>
  ```
*

## Positioning

Positioning is a tricky subject. It's all basically relative, so stay calm and always tinker.

### Static (default

Static is the default positioning it will just be rendered in it's normal flow of the document. Using positioning of the `left` and `right` won't apply to the element that's static.

### Relative

Relative is positioning the upper lefthand corner with respect to an elements containing elements. Note this leaves the space where the element would have been positioned in the dom.

```css
.panel {
  position: relative;
  left: 30px;
  right: 30px;
}
```

[Live Example](https://jsbin.com/xitebetoxa/edit?html,css,output)

The relative positioning can be useful in creating more complex components and will come up a lot when doing small animations.

### Absolute

Absolute positioning is used to position an element relative to the first non-static element that contains it. It does not leave an empty space where the element would have been rendered.

**Relative Positioning leaving an odd blank space**

![Live Example](https://jsbin.com/lekawaxehu/edit?html,css,output)

** Absolute positioning not leaving blank space**

![Live Example](https://jsbin.com/rulorapidu/1/edit?html,css,output)


### Fixed

Fix sticks an element to a specified position.

![Live Example](https://jsbin.com/yeqefokeva/1/edit?html,css,output)

### Exercises

* Make an element with class `content`. Use margins to center it. Give it a width of 80% and background-color of gray.
* Put one paragraph inside the `content` element with some text. Give it background-color of white, width of 50%, and centered margin. What happens if you give it position relative?
* Add another paragraph with class `left` and position `left` of `-20px`.
* Add a `h2` that says `Hello World` in the `content` element with position absolute and `top` of `-10px`.
* Give the `content` class a `margin-top` of `30px`. Observe the changes.
* Make the `content` class have `position` relative. Observe the changes.

## Cascade
CSS is cascading in that elements with the same level of specificity cascade. In other words, if two classes specify style for the same element the one that comes last in the CSS rules wins!

```html
<body>
  <p class="content">
    Hello world
  </p>
</body>
```

Then given the following CSS.

```css
p.content {
  color: blue;
}

p.content {
  color: green
}
```

Since these two css rules are specified for the same element. The one that comes later wins. Thus the text will be green.

Selectors that have the same level of specificity that are less obvious will also follow this rule.

```css
html p.content{
  color: blue;
}

body p.content {
  color: green;
}
```

### Multiple Classes

Elements can also have multiple classes.

```html
<p class="blue red">
</p>
```

If their corresponding CSS rules have the same specificity then the one that comes last wins.

```css
.red {
  color: red;
}

.blue {
  color: blue;
}
```

## Media Queries

You can also define rules for your CSS that only apply for a given media rule. This is super helpful for responsive design.

```css
@media (max-width: 600px) {
  .panel {
    display: none;
  }
}
```

The above rule will hide elements with class `.panel` until the viewport grows larger than `600px`.

```css
@media (min-width: 600px) {
  .panel {
    display: none;
  }
}
```

The above rule will hide elements with class `.panel` for viewports larger than `600px`.

## Import Google Fonts

Using google fonts is easy with CSS3 imports.

```css
/*imports the Open Sans google font*/
@import url('https://fonts.googleapis.com/css?family=Open+Sans');

/*Utilizes the Open Sans google font for all panel elements*/
.panel {
  font-family: 'Open Sans', sans-serif;
}
```
