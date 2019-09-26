# synthesizer-lecture
Synthesizer Lecture
## Getting Started

###### Creating your html file and give it the basic template
You can begin by going to the code pen link that has the editor you will begin to work on


* [First Button](	ttps://codepen.io/Rihzan/pen/LKxJvd)

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

## Making a sound

##### Creating the Keys
To begin you're going to make a list of the keys inside of the `<body>` tag. We will have 13 keys, black and white.

```html
<ul class="set">
      <li class="white c key "  data-key="65"><kbd>A</kbd></li>
      <li class="black cs key " data-key=""><kbd></kbd></li>
      <li class="white d key " data-key=""><kbd></kbd></li>
      <li class="black ds key" data-key=""><kbd></kbd></li>
      <li class="white e key" data-key=""><kbd></kbd></li>
      <li class="white f key" data-key=""><kbd></kbd></li>
      <li class="black fs key" data-key=""><kbd></kbd></li>
      <li class="white g key" data-key=""><kbd></kbd><as/li>
      <li class="black gs key" data-key=""><kbd></kbd></li>
      <li class="white a key" data-key=""><kbd></kbd></li>
      <li class="black as key" data-key=""><kbd></kbd></li>
      <li class="white b key" data-key=""><kbd></kbd></li>
       <li class="white c key" data-key=""><kbd></kbd></li>	
</ul>  
    </ul>
```	
The `data-key` attribute here is a big part of how you will be connecting your keyboard keys to a sound

* <a href="https://www.keycode.info">keycode.info </a> will give you data-key values for every letter on the keyboard



##### Styling your base
You're probably looking at your application saying "That's not a piano!" Dont worry thats what we're getting to next.

You can start by adding a new css file to your project `styles.css` and adding the following css.

```css
* {
  box-sizing:border-box
}

body {
  margin:0;
  background:#222
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
  box-shadow:0 0 50px rgba(0,0,0,0.5) inset,0 1px rgba(212,152,125,0.2) inset,0 5px 15px rgba(0,0,0,0.5)
}

li {
  margin:0;
  padding:0;
  list-style:none;
  position:relative;
  float:left
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
  background:linear-gradient(to bottom,#eee 0%,#fff 100%)
}


.black {
  height:8em;
  width:2em;
  margin:0 0 0 -1em;
  z-index:2;
  border:1px solid #000;
  border-radius:0 0 3px 3px;
  box-shadow:-1px -1px 2px rgba(255,255,255,0.2) inset,0 -5px 2px 3px rgba(0,0,0,0.6) inset,0 2px 4px rgba(0,0,0,0.5);
  background:linear-gradient(45deg,#222 0%,#555 100%)
}
```
Now you should see both black and white keys. But, wait a minute! That's not how a piano looks. We need to add more CSS
to get them positioned the way we want it.

```css
.a,.g,.f,.d,.c {
  margin:0 0 0 -1em
}

ul li:first-child {
  border-radius:5px 0 5px 5px
}

ul li:last-child {
  border-radius:0 5px 5px 5px
}

.ds, .as{
  margin: 0 -2em 0 -1em;
}

.e  {
  margin-right: 16.5px;
}
```
You can see in CSS that we have used the classes from HTML and placed them as selectors

##### Adding Audio to your key

Next you are going to want to add an associating audio sound.

```html
<audio data-key="65" src="http://carolinegabriel.com/demo/js-keyboard/sounds/040.wav"></audio>
```
Notice the same data-key value it matches our first key we created.


##### Playing audio on keypress

Now in order for you to be able to hear anything when that key is pressed youre going to have to add some JavaScript.

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

For sound effects, use these links:


##### Adding "Animation" to your buttons
OK! We now have sound for each key! Let's add some animation to our piano! When a key is pressed on the keyboard,
the associated piano key will move simultaneously. So first things first, we're going to go right back to the `styles.css` file.
We are going to use the classes "black" and "white" to add action.


```CSS

```

