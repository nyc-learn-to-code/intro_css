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
    + [Internal Style](#internal-style)
    + [External CSS](#external-css)

<!-- tocstop -->

## Objectives

## Vocabulary

* **Tag**: The HTML markup representing the start or end of part of a document.

	* The `head` tag is used to denote the start/end of the meta-data of the document.
	* A `body` tag is used to denote the start/end of the content of a document. 
* **Tag Attribute** or **Attribute**: a key and value pair provided on a starting **tag** to extend its definition with meta-data.
	* A common attribute added to a starting `tag` is `class` used to help clarify the semantic purpose of a tag.
		* Help describe the purpose of a paragraph: 
			```
				<p class="comment">Hello World</p>
			```
		* Help describe a section of information. 

			```
				<div class="user-quotes">
				   <p class="quote">Cui Bono</p>
					 <p class="quote">Fortuna est caeca</p> 
				</div>
			``` 
* **Element**: the start and end tags with content between them make up an entire element.
	
	```
		<div class="quote">Hello world</div>	
	```		

* **DOM**: All elements defined in HTML are represented as objects in memory with a collection of attributes and behavior that are initially nested according to the provided HTML file and rooted in a single document object that is drawn on the page. The document can define links to CSS and JS that in utilize the document to select and define properties on various elements that affect appearance or behavior of elements in the HTML. Effectively, the DOM is the current state of the document elements after CSS and JS changes have been applied.

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

#### Internal Style

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

#### External CSS 

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

```
<head>
	<link href="your_style.css" rel="stylesheet">
</head>
```

