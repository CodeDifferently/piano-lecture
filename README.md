# Building a Piano / Synthesizer 


## Project Details
* **Objective** - To build a piano / synthesizer with sound and actionable keys
* **Purpose** - To help students establish familiarity with `HTML` (Hypertext Markup Langauge), `CSS` (Cascading Style Sheets), `JS` (JavaScript).
* **Description** - This guide will walk you through the process to create a piano/sythesizer with sound and actionable keys.
* **Requirements:**
	* About 20 minutes
	* Internet access
	* A text editor or IDE 
		* Check out this free online editor, [Codepen.io](https://codepen.io/)
		








## Project Overview
### Using HTML
* First, using `HTML` will allow you to build a document that can be displayed on a web browser.
* Below is an example of the structure for creating an HTML document.

```HTML 
<!DOCTYPE html>
<html>
	<head>
		<title></title>
	</head>
	<body>
 
	</body>
</html>
```



### Using CSS
* Secondly, you will use `CSS` to describe how HTML elements should be displayed.
* `CSS` allows you the ability to alter colors, fonts, sizes, and so much more.

```CSS
html  {
	background: #000;
}

```



### Using JavaScript
* Lastly, you will use `JavaScript` to make your web page dynamic and create responsive elements.
* For instance, when creating the piano/synthesizer, we want our keys to have action as the keys are the pressed. 

```HTML
 
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script>
```




## Getting Started



### Creating your html file 
We will begin by copying and pasting this into the `HTML` section on CodePen. Everything that will appear on the 
web page is contained by the `<body>` tag. Copy and paste this code in the HTML section of CodePen.


```html 
<!DOCTYPE html>
<html>
	<head>
		<meta charaset="UTF-8">
		<title> Piano/Synthesizer </title>
	</head>
	<body>
	</body>
</html>
```


### Creating the keys
We are going to create a "containter" using the `<section>` tags to nest our `<div>` tags. The `<h1>` tag
will give us a place to title your piano. The `<span>` tag will allow us to make specific changes to that certain text. The `<section>` tag with the attribute class and a value of "wrap", will go inside the `<body>` tag. Everything that is shown on a 
webpage is nested inside of the `<body>` tag. Copy and paste the code below between the opening and closing tags of the 
`<body>` tag.

 


```HTML
<section class="wrap">
  <h1>Name Your Piano</h1>
    <section id="main">
      <div class="nowplaying"></div>
	  <div class="keys">
     <div data-key="65" class="key"> <span class="hints">A</span> </div>
     <div data-key="" class="key sharp"> <span class="hints"> </span> </div>
     <div data-key="" class="key"> <span class="hints"> </span> </div>
     <div data-key="" class="key sharp"> <span class="hints"> </span> </div>
     <div data-key="" class="key"> <span class="hints"> </span> </div>
     <div data-key="" class="key"> <span class="hints"> </span> </div>
     <div data-key="" class="key sharp"> <span class="hints"> </span> </div>
     <div data-key="" class="key"> <span class="hints"> </span> </div>
     <div data-key="" class="key sharp"> <span class="hints"> </span> </div>
     <div data-key="" class="key"> <span class="hints"> </span> </div>
     <div data-key="" class="key sharp"> <span class="hints"> </span> </div>
     <div data-key="" class="key"> <span class="hints"> </span> </div>
     <div data-key="" class="key"> <span class="hints"> </span> </div>
     <div data-key="" class="key sharp"> <span class="hints"> </span> </div>
     <div data-key="" class="key"> <span class="hints"> </span> </div>
     <div data-key="" class="key sharp"> <span class="hints"> </span> </div>
     <div data-key="" class="key"> <span class="hints"> </span> </div>
   </div>
</div>
  </section>
</section>
  

```	
The `data-key` attribute here is a big part of how you will be connecting your keyboard keys to a sound.

* <a href="https://www.keycode.info">keycode.info </a> will give you data-key values for every letter on the keyboard.
Look at the first `<div>` tag. The data-key has a value of "65" which connects to the "A" on our keyboard.
Use that as a guide to connect the other data-key values to other keys on the keyboard. Drop the `<section>` tags in 
the `<body>` tag for it to appear on the web page. On the website, look for the data-key value for the following keys in the
order below. Press the key and the data-key value will appear. Place the value between the two double quotations to give the
data-key attribute a value.  
	
```HTML
W S E D F T G Y H U J K O L P ;
```

After adding the data-key value, nest the keyboard letter inside of the `<span class="hints"> </span>`. 

Your next tag should look like this: `<div data-key="87" class="key sharp"> <span class="hints">W</span> </div>`



### Styling your piano
Your screen should show a list of the letters along with the title. Copy and paste the code below in the CSS section.

```CSS
html  {
    background: #000;
    font-family: 'Noto Serif', serif;
    -webkit-font-smoothing: antialiased;
    text-align: center;
}
	
body {
  background-color: #eee;
}

h1 {
      color: #fff;
      font-family: 'Bungee';
      font-size: 50px;
      font-weight: 400;
      letter-spacing: 0.18em;
      text-transform: uppercase;
      margin: 0;
}	
.nowplaying {
    font-size: 120px;
    line-height: 1;
    color: #eee;
    text-shadow: 0 0 5rem #028ae9;
    transition: all .07s ease;
    min-height: 120px;
}
.keys {
    display: block;
    width: 100%;
    height: 350px;
    max-width: 880px;
    position: relative;
    margin: 40px auto 0;
    cursor: none;
}
.key {
    position: relative;
    border: 4px solid black;
    border-radius: .5rem;
    transition: all .07s ease;
    display: block;
    box-sizing: border-box;
    z-index: 2;
}	
```


### Changing the title
Let's look at making changes to the title. First, let's give our piano a name. Pick whatever you like. To change the title, we 
need to find the heading tag or `<h1>` element. Delete the text inside the opening and closing tags and replace with your
chosen name. Below is what the code will look like. Replace the words "Name Your Piano" with your title.


```HTML
<body>
  <section id="wrap">
      <h1>Name Your Piano</h1>
    <section id="main">
```

### Adding style to the title
Think about various colors you would like to incorporate into your design. We have the ability to change the color, size, font, and more! To make these changes, we need to match up the tag used in HTML for our title with one in CSS. In our HTML document, we used the `<h1>` tag for our title. Next lets match the tag in `HTML` with the tag or selector in the CSS section. 

```CSS
h1 {
      color: #ffffff;
      font-family: 'Bungee';
      font-size: 50px;
      font-weight: 400;
      letter-spacing: 0.18em;
      text-transform: uppercase;
      margin: 0;
      
    }
```
Here we have the selector `<h1>` which has many properties that can be altered. Here we see a property `color` with an
hex value of `#ffffff`, which is white. We can either type the word of the color we want or use the hex value. You can use
Google to search for the hex value of all colors. You can also visit <a href="www.coolors.co">coolors.co</a> Be sure not to
erase the colon before or the semicolon after the value. Adjust each property's value to see the different changes to the 
title. Cool, isn't it?


### Changing the background
Now that you have the title designed, let's look at the background. Since all content displayed on a webpage contained inside
of the `<body>` tag, we will look for the "body" selector in our CSS. You can change to background color using the hex value
or typing the color. 

```CSS
body {
  background-color:#eee;
}
```
Now we have our title and our keys starting to form! You should see all of the letters of the keyboard going down in a row.



### Adding the black and white keys
Copy and paste the code below into the CSS section. Be sure to make sure there is adequate spacing between the ending `}` and 
the next selector. It is important to have code that is readable. The code below will allow our keys to appear.

```CSS
.key:not(.sharp) {
    float: left;
    width: 10%;
    height: 100%;
    background: rgba(255, 255, 255, .8);    
}

.key.sharp {
    position: absolute;
    width: 6%;
    height: 60%;
    background: #818285;
    color: #eee;
    top: 0;
    z-index: 3;
}

.key[data-key="87"] {
    left: 7%;
}

.key[data-key="69"] {
    left: 17%;
}

.key[data-key="84"]  {
    left: 37%;
}

.key[data-key="89"] {
    left: 47%;
}

.key[data-key="85"] {
    left: 57%;    
}

.key[data-key="79"] {
    left: 77%;    
}

.key[data-key="80"] {
    left: 87%;    
}
```
Get ready, we are about to add sound!!!



### Adding audio to your keys

Next, we are going to add an associating audio sound to each key on the piano. We will be using the `<audio>` tag to give our
keys sound. Below is an example of connecting the sound to the "A" key on our keyboard. Copy the code below and paste it under
the last closing `<div>` tag. Looks like this: `</div>`.

```html
<audio data-key="65" src="http://carolinegabriel.com/demo/js-keyboard/sounds/040.wav"></audio>
```

Now let's examine this element. We have an `<audio>` tag with a `data-key` attribute and value. If you notice the value
matches the value we have for the key "A". When the key "A" is pressed on the keyboard, this sound will play. Next there is a
`src` attribute. This is pointing to the location of the sound on the internet.  We are getting even closer to hearing sound!

Here are links to add sound to your piano. Click each link to hear the sound.

For Piano keys in order from left to right:


(A)C = "http://carolinegabriel.com/demo/js-keyboard/sounds/040.wav"

(W)C# = "http://carolinegabriel.com/demo/js-keyboard/sounds/041.wav"

(S)D = "http://carolinegabriel.com/demo/js-keyboard/sounds/042.wav"

(E)D# = "http://carolinegabriel.com/demo/js-keyboard/sounds/043.wav"

(D)E = "http://carolinegabriel.com/demo/js-keyboard/sounds/044.wav"

(F)F = "http://carolinegabriel.com/demo/js-keyboard/sounds/045.wav"

(T)F# = "http://carolinegabriel.com/demo/js-keyboard/sounds/046.wav"

(G)G = "http://carolinegabriel.com/demo/js-keyboard/sounds/047.wav"

(Y)G# = "http://carolinegabriel.com/demo/js-keyboard/sounds/048.wav"

(H)A = "http://carolinegabriel.com/demo/js-keyboard/sounds/049.wav"

(U)A# = "http://carolinegabriel.com/demo/js-keyboard/sounds/050.wav"

(J)B = "http://carolinegabriel.com/demo/js-keyboard/sounds/051.wav"

(K)C = "http://carolinegabriel.com/demo/js-keyboard/sounds/052.wav"

(O)C# = "http://carolinegabriel.com/demo/js-keyboard/sounds/053.wav"

(L)D = "http://carolinegabriel.com/demo/js-keyboard/sounds/054.wav"

(P)D# = "http://carolinegabriel.com/demo/js-keyboard/sounds/055.wav"

(;)E = "http://carolinegabriel.com/demo/js-keyboard/sounds/056.wav"


* Note: To save time and avoid having to type the code over and over, copy and paste the `<audio>` tag for the "A" key. 
Then replace the `data-key` value with the next key's value. Next, copy the associated sound link and paste it over the 
current one. Be sure the link is inside of the double quotations. 


### Playing audio on keypress

Now in order for you to be able to hear anything when the key is pressed, we need to add JavaScript. JavaScript will also 
make our piano keys actionable. In the JS section, copy and paste the code below.

```Javascript 

const keys = document.querySelectorAll(".key"),
  note = document.querySelector(".nowplaying"),
  hints = document.querySelectorAll(".hints");

function playNote(e) {
  const audio = document.querySelector(`audio[data-key="${e.keyCode}"]`),
    key = document.querySelector(`.key[data-key="${e.keyCode}"]`);

  if (!key) return;

  const keyNote = key.getAttribute("data-note");

  key.classList.add("playing");
  note.innerHTML = keyNote;
  audio.currentTime = 0;
  audio.play();
}
window.addEventListener("keydown", playNote);

```

* In short what this does is :
	* lets the window listen for the event `keydown`
	* passes associated `keydown` value from event to the `playSound` function thats called
	* checks if there's an audio and key with the same data-key value as the keypress that was passed along
	* adds class `active` to the key so it can undergo the CSS changes




### Adding "animation" to your keys
We now have sound for each key! Let's add some animation to our piano! When a key is pressed on the keyboard,
the associated piano key will move simultaneously. So first things first. Copy and paste below into the CSS section.

```CSS
.playing {
    transform: scale(.95);
    border-color: #028ae9;
    box-shadow: 0 0 1rem #028ae9;
}

.hints {
    display: block;
    width: 100%;
    opacity: 0;
    position: absolute;
    bottom: 7px;
    transition: opacity .3s ease-out;
    font-size: 20px;
}

.keys:hover .hints {
    opacity: 1;
}
```

Next to have our piano keys return to their original posistion when a key is no longer being pressed, we add the code below. 
Copy and paste the code below under the last statment in the JS section. A statement in JavaScript ends with a semi-colon.

```Javascript

function removeTransition(e) {
  if (e.propertyName !== "transform") return;
  this.classList.remove("playing");
}

function hintsOn(e, index) {
  e.setAttribute("style", "transition-delay:" + index * 50 + "ms");
}

hints.forEach(hintsOn);

keys.forEach(key => key.addEventListener("transitionend", removeTransition));

```
	
And now we have action!!! Want to add a little more pop to your piano? Add the code below to make your title more dynamic.
Placement is crucial so be sure to put the code in the right place. This first bit of code needs to be placed within the `h1`
selector in the CSS. 

```CSS
-webkit-animation: mymove 5s infinite; 
      animation: mymove 5s infinite;
```

`h1` should now look like the code below:

```CSS
 h1 {
      color: blue;
      font-size: 50px;
      font-weight: 400;
      letter-spacing: 0.18em;
      text-transform: uppercase;
      margin: 0;
     -webkit-animation: mymove 5s infinite; 
      animation: mymove 5s infinite;
    }
```   

Next we will add more code to ensure it works properly. Under the `h1` selector's curly brace `}`, copy and paste the code
below.

```CSS
 @-webkit-keyframes mymove {
    75% {font: 40px bold;}
    }
```

Now take a step back and look at your piano! Great job!
