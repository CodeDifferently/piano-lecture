
Synthesizer Lecture
## Getting Started
Log into your CodePen account 

###### Creating your html file and give it the basic template
You can begin by going to the code pen link that has the editor you will begin to work on


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


##### Creating the Keys
To begin, we are going to create a "containter" using the `<section>` tags to hold our `<div>` tags. The `<h1>` tag will give us a place to title your piano. The `<span>` tag will allow us to  `<body>` tag. 

```html
<section class="wrap"
  <h1>Name Your Piano</h1>
    <section id="main">
       <div class="nowplaying"></div>
	  <div class="keys">
	      <div data-key="65" class="key"> <span class="hints">A</span> </div>
		    
	      <div data-key="" class="key sharp" > <span class="hints">W</span> </div>
		    
	      <div data-key="" class="key" > <span class="hints">S</span> </div>
		    
	      <div data-key="" class="key sharp" > <span class="hints">E</span> </div>
		    
	      <div data-key="" class="key" > <span class="hints">D</span> </div>
		    
		<div data-key="" class="key" > <span class="hints">F</span> </div>

		<div data-key="" class="key sharp" > <span class="hints">T</span> </div>

		<div data-key="" class="key" > <span class="hints">G</span> </div>

		<div data-key="" class="key sharp" > <span class="hints">Y</span> </div>

		<div data-key="" class="key" > <span class="hints">H</span> </div>

		<div data-key="" class="key sharp" > <span class="hints">U</span> </div>

		<div data-key="" class="key" > <span class="hints">J</span> </div>

		<div data-key="" class="key" > <span class="hints">K</span> </div>

		<div data-key="" class="key sharp" > <span class="hints">O</span> </div>

		<div data-key="" class="key" > <span class="hints">L</span> </div>
		  
		<div data-key="" class="key sharp" > <span class="hints">P</span> </div>
		  
		<div data-key="" class="key" > <span class="hints">;</span> </div>
      </div>
</div>
```	
The `data-key` attribute here is a big part of how you will be connecting your keyboard keys to a sound.

* <a href="https://www.keycode.info">keycode.info </a> will give you data-key values for every letter on the keyboard.




##### Styling your base
You're probably looking at your application saying "That's not a piano!" Dont worry thats what we're getting to next.

You can start by adding a new css file to your project `styles.css` and adding the following css.

```css
* {
  box-sizing:border-box;
}

body {
  margin:0;
  background:#222;
}

 ul {
  height:18.875em;
  width:37em;
  margin:5em auto;
  padding:3em 0 0 3em;
  position:relative;
  border:1px solid #160801;
  border-radius:1em;
  background:linear-gradient(to bottom right,rgba(0,0,0,0.3)
,rgba(0,0,0,0)),url(https://s3-us-west-2.amazonaws.com/s.cdpn.io/187/vwood.png);
  box-shadow:0 0 50px rgba(0,0,0,0.5) inset,0 1px rgba(212,152,125,0.2) inset,0 5px 15px rgba(0,0,0,0.5);
}

li {
  margin:0;
  padding:0;
  list-style:none;
  position:relative;
  float:left;
}

```
This will give you a base for your piano keys. If you look really close, you will see the letters associated with the keys. 
We will begin to construct the keys next!


##### Adding the black and white keys

```css
ul .white {
  height:16em;
  width:4em;
  z-index:1;
  border-left:1px solid #bbb;
  border-bottom:1px solid #bbb;
  border-radius:0 0 5px 5px;
  box-shadow:-1px 0 0 rgba(255,255,255,0.8) inset,0 0 5px #ccc inset,0 0 3px rgba(0,0,0,0.2);
  background:linear-gradient(to bottom,#eee 0%,#fff 100%);
}


.black {
  height:8em;
  width:2em;
  margin:0 0 0 -1em;
  z-index:2;
  border:1px solid #000;
  border-radius:0 0 3px 3px;
  box-shadow:-1px -1px 2px rgba(255,255,255,0.2) inset,0 -5px 2px 3px rgba(0,0,0,0.6) inset,0 2px 4px rgba(0,0,0,0.5);
  background:linear-gradient(45deg,#222 0%,#555 100%);
}
```



Now you should see both black and white keys. Next we need to add more CSS to get them positioned the way we want it.

```css
.a,.g,.f,.d,.c {
  margin:0 0 0 -1em;
}

ul li:first-child {
  border-radius:5px 0 5px 5px;
}

ul li:last-child {
  border-radius:0 5px 5px 5px;
}

.ds, .as{
  margin: 0 -2em 0 -1em;
}

.e, .b  {
  margin-right: 16.5px;
}

.e{
  margin-left: .75px;
}
```
You can see in CSS that we have used the classes from HTML and placed them as selectors.



##### Adding Audio to your keys

Next you are going to want to add an associating audio sound.

```html
<audio data-key="65" src="http://carolinegabriel.com/demo/js-keyboard/sounds/040.wav"></audio>
```
Notice the same data-key value it matches our first key we created in the list.


##### Playing audio on keypress

Now in order for you to be able to hear anything when that key is pressed, we need to add JavaScript.

Under your `<audio>` tag your going to want to start with your `<script>` tag.

```javascript 
<script>
 function playSound(e) {
 const audio = document.querySelector(`audio[data-key="${e.keyCode}"]`);
 const key = document.querySelector(`li[data-key="${e.keyCode}"]`);
                if (!audio) return;

                key.classList.add('active')
                audio.currentTime = 0;
                audio.play();
            }
 
            window.addEventListener('keydown', playSound);
        </script>
```

* In short what this does is :
	* lets the window listen for the even `keydown`
	* passes associated `keydown` value from event to the `playSound` function thats called.
	* checks if theres an audio and key with the same data-key value as the keypress that was passed along
	* adds class `active` to the key so it can undergo CSS changes
	
	

Now we need to add sounds to the other keys. You can choose to add the sound to the correct piano key or add other sound effects.
For Piano keys:

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






##### Adding "Animation" to your buttons
OK! We now have sound for each key! Let's add some animation to our piano! When a key is pressed on the keyboard,
the associated piano key will move simultaneously. So first things first, we're going to go right back to the `styles.css` file.
We are going to use the classes "black" and "white" to add action.


```CSS

```


