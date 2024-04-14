<b><i>(Aerosmith not Gene Autry)</i></b>
<p>Although I've paused working through the freeCodeCamp course over Easter, I've been scouring my old laptops for the projects that I started towards the end of my degree.</p>
<p>Although there were not that many, they seem to be tilted towards .NET MVC projects, and my time has been occupied with re-familiarising myself with that particular framework/approach</p>
<p>One particularly intriguing snippet was a foray into integrating OAuth into an application - quite why I was investigating this I cannot recall, there must have been a reason, which just illustrates a good reason to document what you are doing and and why!</p>

<img class="image" src="/docs/assets/Screenshot 2024-04-02 221206.png">

<p>The actual OAuth functionality is suspended as I suspect the Authentication services I configured at the time may have expired. <br>The other issue is that at the time I don't appear to have set up any password recovery option for the log-in!</p>
<p>Anyway, returning to the task in hand, nanely understanding do-while statements in C#</p>

    using System.Runtime.CompilerServices;

    string? readResult; 
Declares a nullable string variable named readResult. Nullable strings can hold a string value or a null reference.

    string valueEntered ="";

Declares an empty string variable named valueEntered.
    
    int numValue =0;
Declares an integer variable named numValue and initializes it to 0.

    bool validNumber = false;
Declares a boolean variable named validNumber and initializes it to false.
    
So, the first part involves declaring the variables we are going to use and, where neccessary initializing them. <br>Notice the "<b>?</b>" for the <b>readResult</B> variable, which allows a "<a href="https://letoilenoir.github.io/2024/03/26/Nothing-really-matters.html">null</a>" entry   

    Console.WriteLine("Enter a number between 5 and 10:");
    
<p>This is the request for the user to provide input.</p>
    
    do
    {
Starts a do-while loop, ensuring the <a href="https://exceptionnotfound.net/csharp-in-simple-terms-5-basic-statements-and-loops/">code block</a> inside the loop executes at least once.

        readResult = Console.ReadLine();
Reads the input from the user via the console and assigns it to the readResult variable.

        if (readResult !=null)
    {
        valueEntered = readResult;
    }
Checks if readResult is not null. If it's not null, assigns its value to valueEntered.
     
    validNumber = int.TryParse(valueEntered, out numValue);

Attempts to parse the string stored in valueEntered into an integer. If successful, assigns the parsed integer value to numValue and sets validNumber to true. Otherwise, validNumber remains false.



      if (validNumber == true)
      { 
Checks if validNumber is true.

     if (numValue <= 5 || numValue >= 10)
     {
     validNumber = false;
     Console.WriteLine($"You entered {numValue}.Please enter a number between 5 and 10");
     }


Checks if numValue is less than or equal to 5 or greater than or equal to 10. If true, sets validNumber to false and prompts the user to enter a number between 5 and 10.

    } 
    else
    {  
        Console.WriteLine("Sorry you entered an invalid number. Please try again");
        
If validNumber is false, outputs a message indicating that the user entered an invalid number.
    }
    } while (validNumber == false);

    Console.WriteLine($"Your input value ({numValue}) has been accepted.");

    readResult = Console.ReadLine();

    </p>
