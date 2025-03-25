Following on from the stand alone Chords Python script, although the tkinter GUI is adequate, a more polished interface may be appropriate for a web based application. <br>
Below are are two variations created using the <a href="https://github.com/pygame/pygame">pygame</a> library<br> 
<img class="image" src="/docs/assets/UI.png" width = "100%"><br>
There are also a couple of enhancements made from the original <a href="https://github.com/Letoilenoir/chord/blob/main/chordTen.py">Chords</a> script, although the prototypes displayed are still purely python scripts, they have a more interactive feel.

Both contain options to create chord progressions with or without key signatures.<br>
Both show the selections added to the progression in the "Current Progression" frame<br>
When chosing to use a chord progression the first will display the only the root notes available in that key signature:
<img class="image" src="/docs/assets/ui1.png" width = "100%"><br>
By selecting and and adding one to the progression, the next root note in the scale will automatically be highlighted:
<img class="image" src="/docs/assets/ui2.png" width = "100%"><br>
<b>NB: This function does NOT automatically create a coherent progression according to Music Theory as yet, it only presents the possible root notes that are included in the chosen Key Signature<b><br>

When chosing not to use a Key Signature the entire range of root notes are available:
<img class="image" src="/docs/assets/ui3.png" width = "100%"><br>
When selecting and  adding one to the progression, no suggested subsequent root note is displayed:
<img class="image" src="/docs/assets/ui4.png" width = "100%"><br>
<br>
<br>
The second version has the same functionality i.e you can choose to create a progression with opr without selecting a key signature<br>
<img class="image" src="/docs/assets/ui5.png" width = "100%"><br>
<br>
Again, the choice of root notes will be restricted to those in the key signature:<br>
<img class="image" src="/docs/assets/ui6.png" width = "100%"><br>
<BR>
Strictly speaking, when creating a progression using a key signature the type of chord should also be restricted:<br>
<img class="image" src="/docs/assets/ui6.png" width = "100%"><br>




