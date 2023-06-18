# files / System.IO

**for today im changing my submission format to be exactly as the notes i took during the lecture please if they need additional work inform me**
we use files for permanant storage for logging actions on my website/ store images and files from users

define a string to hold the path

add

    using System.IO;
at the begining of the program to be access the built in methods

in a new method that takes the path i stored call

    File.ReadAllText(path);

from here we can use a normal

    Console.Write();

when adding a new file (data.txt) inside the folder of my project the default path is step outside folder 3 times ("../../../data.txt") in order to access

sometimes when reading images i need to convert it to a RawFile like so (future proofing)

    byte[] data = File.ReadAllBytes(path);
    foreach (byte b in data){
        Console.WriteLine(b);
}

 we can overwrite the previous content of a text file by using

    File.WriteAllText(path,newLine);
