
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
Look at the third `<div>` tag. The data-key has a value of "65" which connects to the "A" on our keyboard.
Use that as a guide to connect the other data-key values to other keys on the keyboard




##### Styling your base
You're probably looking at your application saying "That's not a piano!" Dont worry thats what we're getting to next.

You can start by adding a new css file to your project `styles.css` and adding the following css.

```css
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
      color: #fff;
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
Now we have our title and our keys starting to form! You should see all of the letters of the keyboard going down in a row.




##### Adding the black and white keys

```css
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

Now you should be able to see the black and white keys. Next steps will be to add the sounds!




##### Adding Audio to your keys

Next you are going to want to add an associating audio sound. Under the last `<div>` tag, we will use the `<audio>` tag 
to give our keys sound! Below is an example of connecting the sound to the "A" key on our keyboard.

```html
<audio data-key="65" src="http://carolinegabriel.com/demo/js-keyboard/sounds/040.wav"></audio>
```
Notice the same data-key value it matches our first key we created in the list. We are getting even closer hearing the sound!

Here are links to add sound to your piano. You can choose the traditional piano notes to your keys or add in 
instrumental sound effects! Click each link to each the sound.

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




##### Playing audio on keypress

Now in order for you to be able to hear anything when that key is pressed, we need to add JavaScript. 


Under your `<audio>` tag your going to want to start with your `<script>` tag.

```javascript 
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




##### Adding "Animation" to your buttons
OK! We now have sound for each key! Let's add some animation to our piano! When a key is pressed on the keyboard,
the associated piano key will move simultaneously. So first things first, we're going to go right back to the `styles.css` file and add the code below.


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











