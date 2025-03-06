<img class="image" src="/docs/assets/Flask_logo.png" width = "50%">

Following of from introducing the Chord Python Script, I decided to investigate the possibility of hosting the script via FLASK

Although this tutorial <a href="https://realpython.com/python-web-applications/">Python Web Applications: Deploy Your Script as a Flask App</a> is now a few years old, it provided a guide to the steps involved in setting this up.<br><BR>
I had to spend some time sorting out the Python installation as apparently there is a known issue with version from Microsoft Store<br> This entailed removing the installed ones, as well as removing registry keys that kept invoking the MS version.

Having successfully instaled the Python Foundation version, the virtual environment was created using this command:
 
    python -m venv venv

and finally activated:

    venv\Scripts\activate

Once the virtual environment was running, Flask & Werkzeug needed to be updated:

    pip install --upgrade flask werkzeug

Once run, the latest version of Flask was revealed to be

    Successfully installed flask-3.1.0

The version in the instructions <i>(requirements.txt)</i> is <b>Flask==2.1.2 </b> so this file was also edited to hopefully prevent this occuring.

Having made the neccesary adjustments, running the command

    python main.py

returned the confirmation
   
    * Serving Flask app 'main'
    * Debug mode: on
    WARNING: This is a development server. Do not use it in a production deployment. Use a production WSGI server instead.
    * Running on http://127.0.0.1:8080
    Press CTRL+C to quit
    * Restarting with stat
    * Debugger is active!
    * Debugger PIN: ***-***-***

Pasting the address into the browser returned the app on the web:<br>

<img class="image" src="/docs/assets/localRun.png" width = "50%">
    


    



