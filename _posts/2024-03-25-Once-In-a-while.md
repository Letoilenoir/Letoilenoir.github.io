
The code below generates a list of random numbers between 1 to ten, until the number 7 is generated:

    using System.Runtime.CompilerServices;

    Random random = new Random();
    int current = 0;

    do
    {
        current =random.Next(1, 11);
        Console.WriteLine(current);
    } while (current !=7);

#Hero Monster challenge

NB: the comments in the code that follows are a personal "aide memoire" and should not be viewed as canonical truths!

    using System.Collections;
    using System.Data;

    int hero =10                        //initialise the hero's starting healthscore
    int monster -10                     //initialise the monster's starting healthscore
    Random dice = new Random ();        //set up a random dice throw

    do//using a do statement in the outside loop ensures that the code runs at least once
    {
    int roll = dice.Next(1,11);         //this initates the first roll of the dice between 1-10
    monster -=roll;                     //this deducts the value of the roll above from the monsters healthscore

    Console.Writeline($"Monster was damaged  and lost {roll} health and now has {monster} health,");

    // this writes out that the monster lost the value of the dice roll and what the monsters healthscore now is

     if(monster >0) continue;               //if the monsters health is greater than zero the script continues

     roll =dice.Next(1, 11);                //if the sctript continues then a further dice roll is instigated
     hero -=roll;                           //this time the value of the dice is deducted from the hero's healthscore
     
     Console.Writeline($"Hero was damaged  and lost {roll} health and now has {hero} health,");

     // this writes out that the hero lost the value of the dice roll and what the hero's healthscore now is
     
     } while (hero > 0 && monster >0);     
     
     //having initiated the contest the sequence continues as long as both healthscores are greater than zero
 
