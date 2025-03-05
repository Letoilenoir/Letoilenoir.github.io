Chord - generate Chord/Chord Sequences to MIDI files
<h1>Chord Generator (chordTen.py)</h1>
*Re-dated to reflect correct date*
A small Python script for download.<br>
Will generate either a single chord or a chord progression, allow the user to name the output and save to the same directory that contains the script itself.<br>
Also gives the option of opening the newly created midi file in MuseScore Studio 4 or Windows Player Legacy
<img class="image" src="/docs/assets/Chord0.png" width = "100%">
<img class="image" src="/docs/assets/ChordTen.png" width = "100%">

<br>

On executing the script a UI screen opens to allow the user to input the first parameters:<br>

<img class="image" src="/docs/assets/Chord1.png" width = "100%">
The process is fairly intuitive, the user enters the root note of the first chord.
Currently the accepted inputs are A,B,C,D,E,F,G plus sharps (#) where music notation is applicable - there is currently no text support to allow input for "flat" notes:
<img class="image" src="/docs/assets/Chord2.png" width = "100%">
With the root selected the user can then select the chord type:
<img class="image" src="/docs/assets/Chord3.png" width = "100%">

<img class="image" src="/docs/assets/Chord4.png" width = "100%">
Then the duration can be set (currently 1 = one crotchet/quarter note):
<img class="image" src="/docs/assets/Chord5.png" width = "100%">
Clicking on "Generate Chord" will bring up a prompt to add another chord: 
<img class="image" src="/docs/assets/Chord6.png" width = "100%">
If the usere wants to continue building a sequence they repeat the above sequence
<img class="image" src="/docs/assets/Chord7.png" width = "100%">
Once the User chooses to end the input they are presented with an option to give the progression a name
<img class="image" src="/docs/assets/Chord8.png" width = "100%">
Clicking "Okay" will save the MIDI file into the same directory that hosts the script and also options to open the MIDI in either MuseScore Studio 4 or Windows Media Player Legacy
<img class="image" src="/docs/assets/Chord9.png" width = "100%">

<img class="image" src="/docs/assets/MuseScore4.png" width = "100%">
<img class="image" src="/docs/assets/WinPlay.png" width = "100%">

There is currently no progression suggestions, no support for time signatures, no support for triplets = the idea is simply to provide a quick and easy way to get a skeleton of your peice into a mid format for you to use in a DAW


