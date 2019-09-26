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
To begin you're going to make a list of the keys. We will have 13 keys, black and white.

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
       <li class="white c-oct key" data-key=""><kbd></kbd></li>	
</ul>  
    </ul>
```	
the `data-key` attribute here is a big part of how you will be connecting your keyboard keys to a sound

* <a href="https://www.keycode.info">keycode.info </a> will give you data-key values for every letter on the keyboard

##### Adding Audio to your key

Next you are going to want to add an associating audio sound

```html
<audio data-key="65" src="http://carolinegabriel.com/demo/js-keyboard/sounds/040.wav"></audio>
```
Notice the same data key value it matches our button we previously created.
