<b><i>(Aerosmith not Gene Autry)</i></b>
<p>Although Ive paused working through the freeCodeCamp course over Easter, I've been scouring my old laptops for the projects that I started towards the end of my degree.</p>
<p>Although there were not that many, they seem to be tilted towards .NET MVC projects, and my time has been occupied with re-familiarising my self with that particular framework approach</p>
<p>One particularly intriguing snippet weas a foray into imtegtratiung OAuth into an application - quite why I was investigating this I cannot recall, there must have been a reason, which just provides a good reason to document what I was doing and why!</p>
<p>So returning to the task in hand, nanely understanding do-while statements in C#</p>

    using System.Runtime.CompilerServices;

    string? readResult;
    string valueEntered ="";
    int numValue =0;
    bool validNumber = false;
    
So the first part involves declaring the variables we are going to use. Notice the "<b>?</b>" for the <b>readResult</B> variable, which allows a "<a href="https://letoilenoir.github.io/2024/03/26/Nothing-really-matters.html">null</a>" entry   

    Console.WriteLine("Enter a number between 5 and 10:");
    
<p>This is the request for the user to provide input.</p>
    
    do
    {
        readResult = Console.ReadLine();
        if (readResult !=null)
    {
        valueEntered = readResult;
    }
     
     validNumber = int.TryParse(valueEntered, out numValue);

    if (validNumber == true)
    {
        if (numValue <= 5 || numValue >= 10)
        {
            validNumber = false;
            Console.WriteLine($"You entered {numValue}.Please enter a number between 5 and 10");
        }

    } 
    else
    {  
        Console.WriteLine("Sorry you entered an invalid number. Pleese try again");
    }
    } while (validNumber == false);

    Console.WriteLine($"Your input value ({numValue}) has been accepted.");

    readResult = Console.ReadLine();

    </p>
