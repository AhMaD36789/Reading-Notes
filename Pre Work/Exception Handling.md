# Exception Handling

The following will detail a clear and consise method for debugging

* What did you expect your code to do?

* What happened instead?

* Are you using the right (API/object/function/method/property) ?

* Does your code contain typos (unlikly due to visual studio and similar applications typo detection)

* Did you make a recent code change in an assumed unrelated area ?

* Did an unexpected value get passed ?

* Do you know the intent of the code ? (check comments and readme when debugging some else's code)

## WHATS NEXT?

After running through these questions if you still can't identify an area where the bug is happening utalize the debugging mode and breakpoints to check how your code is getting executed line by line and inspect variables to check how thier values change as the program is being executed

## HOW TO AVOID IN THE FUTURE

There is this neat menthod is Visual Studio called Try Catch methed. which encapsulates the new code you're trying to make and throws exceptions to the catch method. at the end of a try catch block you can add a finally statement to notify you that this code segmant has been run or to show a message to the user

### IMPLEMENTATION

I will apply a try catch on a hello world application to show the format

try{
    Console.WriteLine("Hello World");
}
catch(Exception ex){
    Console.WriteLine(ex.message);
}
finally {
    Console.WriteLine("execution complete");
}

so lets break it down by order of simplicity

finally will always be executed regardless if an error gets caught or not

try is testing my hello world to check if anything wrong will happen

now for the interesting part the catch. if something goes wrong the error will be caught a new variable named ex will be defined with a class of Exception and the error message will be printed

## CATASTROPHIC FAILURES OF THE PAST

### Ariane 5

A data conversion from 64-bit floating-point value to 16-bit signed integer value to be stored in a variable representing horizontal bias caused a processor trap (operand error) because the floating-point value was too large to be represented by a 16-bit signed integer.

### Therac-25

Two software faults were to blame. One, when the operator incorrectly selected X-ray mode before quickly changing to electron mode, which allowed the electron beam to be set for X-ray mode without the X-ray target being in place. A second fault allowed the electron beam to activate during field-light mode, during which no beam scanner was active or target was in place.

The high-current electron beam struck the patients with approximately 100 times the intended dose of radiation, and over a narrower area, delivering a potentially lethal dose of beta radiation.
