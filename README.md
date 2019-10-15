# Building a Piano / Synthesizer 


## Project Details
* **Objective** - To build a piano / synthesizer with sound and actionable keys
* **Purpose** - To help students establish familiarity with `HTML` (Hypertext Markup Langauge), `CSS` (Cascading Style Sheets), `JS` (JavaScript).
* **Description** - This guide will walk you through the process to create a piano/sythesizer with sound and actionable keys.
* **Requirements:**
	* About 20 minutes
	* Internet access
	* A text editor or IDE 
		* Check out this free online editor, [Codepen.io](https://codepen.io/codeacct/pen/mddyYPo)
		








## Project Overview
### Using HTML
* First, using `HTML` will allow you to build a document that can be displayed on a web broswer.
* Below is an example of the structure for creating an HTML document.

```HTML 
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



### Using CSS
* Secondly, you will use `CSS` to describe how HTML elements should be displayed.
* `CSS` allows you the ability to alter colors, fonts, sizes, and so much more.

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
    font-size: 50px;
    font-weight: 400;
    letter-spacing: 0.18em;
    text-transform: uppercase;
    margin: 0;
}
```



### Using JavaScript
* Lastly, you will use `JavaScript` to make your web page dynamic and create responsive elements.
* For instance, when creating the piano/synthesizer, we want our keys to have action as the keys are the pressed. 

```JavaScript
function playNote(e) {
  const audio = document.querySelector(`audio[data-key="${e.keyCode}"]`),
    key = document.querySelector(`.key[data-key="${e.keyCode}"]`);

  if (!key) return;


  key.classList.add("playing");
  audio.currentTime = 0;
  audio.play();
}
```


## Getting Started



#### Creating your html file 
We will begin by copying and pasting this into the `HTML` section on CodePen. Everything that will appear on the 
web page is contained by the `<body>` tag.


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


#### Creating the keys
We are going to create a "containter" using the `<section>` tags to hold our `<div>` tags. The `<h1>` tag
will give us a place to title your piano. The `<span>` tag will allow us to make specific changes to certain text. The `<section>` tag 
with a class of "wrap", will go inside the `<body>` tag. 
 


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
Use that as a guide to connect the other data-key values to other keys on the keyboard. Drop the `<section>` tags in the `<body>` tag
for it to appear on the web page. 




#### Styling your piano
You're probably looking at your application saying "That's not a piano!" Dont worry thats what we're getting to next.

You can start by adding a new css file to your project `styles.css` and adding the following `CSS`.

```CSS
html  {
    background: #000;
    font-family: 'Noto Serif', serif;
    -webkit-font-smoothing: antialiased;
    text-align: center;
}
	
body {
  background-color: #ff8400;
}

h1 {
    color: ;
    font-size: ;
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

Now we have our title and our keys starting to form! You should see all of the letters of the keyboard going down in a row.



#### Adding the black and white keys
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

You should now be able to see the black and white keys. We can make changes to the title, the background, and the color of the keys To make these changes, let's head to `style.css` to make these changes.



#### Changing the title
Let's first look at making changes to the title. Think about various colors you would like to incorporate into your design. 
Next lets match the tag in `HTML` with the selector in our `style.css`. We can also change the font size.

```HTML
<body>
  <section id="wrap">
      <h1>Name Your Piano</h1>
    <section id="main">
```

```CSS
h1 {
      color: #fff;
      font-family: 'Bungee';
      font-size: 50px;
      font-weight: 400;
      letter-spacing: 0.18em;
      text-transform: uppercase;
      margin: 0;
      
    }
```
In the `style.css` you have the option to alter the type of font, color, spacing, and how bold it appears. Adjust each one of them 
to see the different changes. Cool, isn't it?


#### Changing the background
Now that you have the title designed, let's look at the background. Since everything displayed on a webpage must be inside of the 
`<body>` tag, we will look for the "body" selector in our `style.css`. Here we see a property `background-color` with an hex value of
`#eee`, which is white. We can either type the word of the color we want or use the hex value. You can use Google to search for the hex 
value of all colors.

```CSS
body {
  background-color:#eee;
}
```
Get ready, we are about to add sound!!!



#### Adding audio to your keys

Next, we are going to want to add an associating audio sound to each key on the piano. Under the last `</div>` tag, 
we will use the `<audio>` tag to give our keys sound! Below is an example of connecting the sound to the "A" key on our keyboard.

```html
<audio data-key="65" src="http://carolinegabriel.com/demo/js-keyboard/sounds/040.wav"></audio>
```

Notice the same data-key value it matches our first key we created in the list. We are getting even closer hearing the sound!

Here are links to add sound to your piano. You can choose the traditional piano notes to your keys or add in 
instrumental sound effects! Click each link to hear the sound.

For Piano keys in order from left to right:

C = "http://carolinegabriel.com/demo/js-keyboard/sounds/040.wav"

C# = "http://carolinegabriel.com/demo/js-keyboard/sounds/041.wav"

D = "http://carolinegabriel.com/demo/js-keyboard/sounds/042.wav"

D# = "http://carolinegabriel.com/demo/js-keyboard/sounds/043.wav"

E = "http://carolinegabriel.com/demo/js-keyboard/sounds/044.wav"

F = "http://carolinegabriel.com/demo/js-keyboard/sounds/045.wav"

F# = "http://carolinegabriel.com/demo/js-keyboard/sounds/046.wav"

G = "http://carolinegabriel.com/demo/js-keyboard/sounds/047.wav"

G# = "http://carolinegabriel.com/demo/js-keyboard/sounds/048.wav"

A = "http://carolinegabriel.com/demo/js-keyboard/sounds/049.wav"

A# = "http://carolinegabriel.com/demo/js-keyboard/sounds/050.wav"

B = "http://carolinegabriel.com/demo/js-keyboard/sounds/051.wav"

C = "http://carolinegabriel.com/demo/js-keyboard/sounds/052.wav"

C# = "http://carolinegabriel.com/demo/js-keyboard/sounds/053.wav"

D = "http://carolinegabriel.com/demo/js-keyboard/sounds/054.wav"

D# = "http://carolinegabriel.com/demo/js-keyboard/sounds/055.wav"

E = "http://carolinegabriel.com/demo/js-keyboard/sounds/056.wav"


For instrumental sound effects, use these links. You can click each link to hear the sound.

"https://s3.amazonaws.com/freecodecamp/drums/Heater-1.mp3"

"https://s3.amazonaws.com/freecodecamp/drums/Heater-1.mp3"

"https://s3.amazonaws.com/freecodecamp/drums/Kick_n_Hat.mp3"

"https://res.cloudinary.com/cd0hgkqgk/video/upload/v1538335238/audio/nipon_cymbal_1.mp3"

"https://res.cloudinary.com/cd0hgkqgk/video/upload/v1538335237/audio/nipon_cymbal_2.mp3"

"https://res.cloudinary.com/cd0hgkqgk/video/upload/v1538335238/audio/taiko_2.mp3"

"https://res.cloudinary.com/cd0hgkqgk/video/upload/v1538335237/audio/med_taiko.mp3"

"https://res.cloudinary.com/cd0hgkqgk/video/upload/v1538335238/audio/shime_hi.mp3"

"https://res.cloudinary.com/cd0hgkqgk/video/upload/v1538335238/audio/shime_hi_2.mp3"

"https://s3.us-east-2.amazonaws.com/fcc-projects-jms/Drum+Machine/Conga.m4a"

"https://s3.us-east-2.amazonaws.com/fcc-projects-jms/Drum+Machine/Crash.m4a "

"https://s3.us-east-2.amazonaws.com/fcc-projects-jms/Drum+Machine/Cymbal+Hit.m4a"

"https://s3.us-east-2.amazonaws.com/fcc-projects-jms/Drum+Machine/Scratch.m4a"

"https://s3-us-west-2.amazonaws.com/s.cdpn.io/377560/PAD1.wav"

"https://s3-us-west-2.amazonaws.com/s.cdpn.io/377560/HORN1.wav"




#### Playing audio on keypress

Now in order for you to be able to hear anything when that key is pressed, we need to add JavaScript. 


Under your `<audio>` tag we are going to start with a `<script>` tag.

```HTML 
<script>
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
</script>
```

* In short what this does is :
	* lets the window listen for the even `keydown`
	* passes associated `keydown` value from event to the `playSound` function thats called.
	* checks if theres an audio and key with the same data-key value as the keypress that was passed along
	* adds class `active` to the key so it can undergo CSS changes




#### Adding "animation" to your keys
OK! We now have sound for each key! Let's add some animation to our piano! When a key is pressed on the keyboard,
the associated piano key will move simultaneously. So first things first, we're going to go right back to the`styles.css`
file and add the code below.


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

And now we have action!!! Want to add a little more pop to your piano? Add the code below to make your title more dynamic. Placement is
crucial so be sure to put the code in the right place. This first bit of code needs to be placed within the `h1` selector in the CSS. 

```CSS
-webkit-animation: mymove 5s infinite; 
      animation: mymove 5s infinite;
```

`h1` should now look like this:

```CSS
 h1 {
      color: #fff;
      font-size: 50px;
      font-weight: 400;
      letter-spacing: 0.18em;
      text-transform: uppercase;
      margin: 0;
     -webkit-animation: mymove 5s infinite; 
      animation: mymove 5s infinite;
    }
```   

Next we will add more code to ensure it works properly. Under the `h1` selector, copy and paste the code below.

```CSS
 @-webkit-keyframes mymove {
    75% {font: 40px bold;}
    }
```

Now take a step back and look at your piano! Great job!
