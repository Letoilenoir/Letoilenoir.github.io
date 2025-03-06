<img class="image" src="/docs/assets/Flask_logo.png" width = "100%">

Following of from introducing the Chord Python Script I decided to investigate the possibility of hosting the script via FLASK

Although this tutorial <a href="https://realpython.com/python-web-applications/">Python Web Applications: Deploy Your Script as a Flask App</a> is now a few years old it provided a guide to the steps involved in setting this up.<br><BR>
I had to spend some time sorting out the Python installation as apparently there is a known issue with version from Microsoft Store<br> This entailed removing the installed ones, as well as removing registry keys that kept invoking the MS version.

Having successfully instaled the Python Foundation version the virtual environment, was created using this command:

 
    
    python -m venv venv

 
and finally activated:

    venv\Scripts\activate

Once the virtual environment was running Flask & Werkzeug needed to be updated:

    pip install --upgrade flask werkzeug



