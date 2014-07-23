#Web Audio API tutorial

###Preparation
* Fork this project on github to have the basic styles and markup.

* Have the [Mozilla](https://developer.mozilla.org/en-US/docs/Web/API/AudioContext) 
and [Web Audio](http://webaudio.github.io/web-audio-api/) documentation open. 

* jQuery is already included on the page

###To start

Create an `AudioContext` on page load.  This will be the controller for all of the sound generation, any effects you apply, and routing the sound out through your speakers. You only need to create one context for the page. Ensure that it supports different browsers, and provides a message for the user if their browser doesn’t support the Web Audio API.

###Playing a sound
* Create a function called `playSound()`
* Create a temporary button on your page, and call `playSound` when the button is clicked. 
* Inside the function, create a sound wave using `createOscillator`. You won’t be able to hear sound yet. ([documentation](https://developer.mozilla.org/en-US/docs/Web/API/AudioContext.createOscillator))

* Connect the oscillator out to your speakers, so that you can hear the sound when you click the button. It will only work once per page load for now.
* Make the note play for one second. Note that time in the Web Audio API is defined in seconds, not milliseconds like you normally would use in JavaScript.
* Change the start and end time of the note playing to take into account the `currentTime` of the `AudioContext`. It should play for one second every single time you click the button. ([documentation](https://developer.mozilla.org/en-US/docs/Web/API/AudioContext.currentTime))
* Change the volume of the note to be 1% of the current volume. 
* Change the volume so that it is loudest at 0.125 seconds, and then fades out. You may have to do this in phases. ([documentation](http://webaudio.github.io/web-audio-api/#the-audioparam-interface))
* You may also hear some “clicking” at the start of the note. You can fix it by playing the note at very low volume at first, then increasing it.

###Playing different notes
* You can change the tone of the note by adjusting the frequency on the `OscillatorNode`. The frequency is defined in Hertz. You can look up a [list of notes](http://www.phy.mtu.edu/~suits/notefreqs.html) to find standard note frequencies.
* Choose 16 different note frequencies, and add them to an array. You can select any notes you like!  I recommend sticking to a music scale of defined notes (e.g. a [major scale](http://www.musictheorysite.com/major-scales/list-of-all-major-scales) for a “happy” sound, minor scale for a “sad” sound, or [pentatonic scale](http://www.musictheorysite.com/pentatonic-scales) for harmonious sound) 
* As a test, loop over your array of notes and play them when you click the button. Stagger the notes by half a second each, so that you can hear a scale. You can either use `setTimeout`, or adjust the start time relative to `currentTime`.


###Building up the grid
* Add one `div` inside the existing “grid” div on the page, and put 16 checkboxes inside it. The checkboxes should all have the class “button”. Give each checkbox a value between 0 and 15. They will already be styled for you (hooray!) so they should appear as a vertical slice of boxes.  
* Change your loop of notes to play all of the notes at the same time, like a chord instead of a scale. put the loop inside a function called `playColumn()`.
* Now, instead of playing all notes, assign each checkbox to a note, and play only the notes that have a corresponding checkbox ticked. You might use jQuery here to help. 
* Use a `setTimeout` to play the column of notes repeatedly every two seconds. 
* Now, add 15 more divs with checkboxes inside them :) you should have a 16 x 16 grid 
* Set each grid column to start playing with a 0.125s difference between each.  
* Remove the temporary button, and make the columns start playing on pageLoad.

### You're done!
Feedback, improvements and pull requests are welcome, especially for styling ;)