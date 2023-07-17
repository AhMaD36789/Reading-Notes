# Topics

- ## File and Stream I/O

- ## How to: Write text to a file

- ## How to: Read and write to a newly created data file

### File and Stream I/O summary

#### Files and directories

For path naming conventions and the ways to express a file path for Windows systems, including with the DOS device syntax supported in .NET Core .NET Framework

Here are some commonly used file and directory classes:

File - provides static methods for creating, copying, deleting, moving, and opening files, and helps create a FileStream object.

FileInfo - provides instance methods for creating, copying, deleting, moving, and opening files, and helps create a FileStream object.

Directory - provides static methods for creating, moving, and enumerating through directories and subdirectories.

DirectoryInfo - provides instance methods for creating, moving, and enumerating through directories and subdirectories.

Path - provides methods and properties for processing directory strings in a cross-platform manner.

#### Streams

The abstract base class Stream supports reading and writing bytes. All classes that represent streams inherit from the Stream class. The Stream class and its derived classes provide a common view of data sources and repositories, and isolate the programmer from the specific details of the operating system and underlying devices.

Streams involve three fundamental operations:

Reading - transferring data from a stream into a data structure, such as an array of bytes.

Writing - transferring data to a stream from a data source.

Seeking - querying and modifying the current position within a stream.

Here are some commonly used stream classes:

FileStream – for reading and writing to a file.

IsolatedStorageFileStream – for reading and writing to a file in isolated storage.

MemoryStream – for reading and writing to memory as the backing store.

BufferedStream – for improving performance of read and write operations.

NetworkStream – for reading and writing over network sockets.

PipeStream – for reading and writing over anonymous and named pipes.

CryptoStream – for linking data streams to cryptographic transformations.

#### Readers and writers

Here are some commonly used reader and writer classes:

BinaryReader and BinaryWriter – for reading and writing primitive data types as binary values.

StreamReader and StreamWriter – for reading and writing characters by using an encoding value to convert the characters to and from bytes.

StringReader and StringWriter – for reading and writing characters to and from strings.

TextReader and TextWriter – serve as the abstract base classes for other readers and writers that read and write characters and strings, but not binary data.

#### Asynchronous I/O operations

You should perform these tasks asynchronously if your application needs to remain responsive to the user. With synchronous I/O operations, the UI thread is blocked until the resource-intensive operation has completed.

#### Compression

The following classes are frequently used when compressing and decompressing files and streams:

ZipArchive – for creating and retrieving entries in the zip archive.

ZipArchiveEntry – for representing a compressed file.

ZipFile – for creating, extracting, and opening a compressed package.

ZipFileExtensions – for creating and extracting entries in a compressed package.

DeflateStream – for compressing and decompressing streams using the Deflate algorithm.

GZipStream – for compressing and decompressing streams in gzip data format.

#### Isolated storage

The following classes are frequently used when implementing isolated storage:

IsolatedStorage – provides the base class for isolated storage implementations.

IsolatedStorageFile – provides an isolated storage area that contains files and directories.

IsolatedStorageFileStream - exposes a file within isolated storage.

#### I/O and security

When you use the classes in the System.IO namespace, you must follow operating system security requirements such as access control lists (ACLs) to control access to files and directories. This requirement is in addition to any FileIOPermission requirements.

### How to: Write text to a file summary

The following classes and methods are typically used to write text to a file:

StreamWriter contains methods to write to a file synchronously (Write and WriteLine) or asynchronously (WriteAsync and WriteLineAsync).

File provides static methods to write text to a file such as WriteAllLines and WriteAllText, or to append text to a file such as AppendAllLines, AppendAllText, and AppendText.

Path is for strings that have file or directory path information. It contains the Combine method and in .NET Core 2.1 and later, the Join and TryJoin methods. These methods let you concatenate strings for building a file or directory path.

#### Example: Synchronously write text with StreamWriter

    using System;
    using System.IO;

    class Program
    {
    static void Main(string[] args)
    {

        // Create a string array with the lines of text
        string[] lines = { "First line", "Second line", "Third line" };

        // Set a variable to the Documents path.
        string docPath =
          Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments);

        // Write the string array to a new file named "WriteLines.txt".
        using (StreamWriter outputFile = new StreamWriter(Path.Combine(docPath, "WriteLines.txt")))
        {
            foreach (string line in lines)
                outputFile.WriteLine(line);
        }
    }
    }
    // The example creates a file named "WriteLines.txt" with the following contents:
    // First line
    // Second line
    // Third line

#### Example: Asynchronously write text with StreamWriter

    using System;
    using System.IO;
    using System.Threading.Tasks;

    class Program
    {
    static async Task Main()
    {
        // Set a variable to the Documents path.
        string docPath = Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments);

        // Write the specified text asynchronously to a new file named "WriteTextAsync.txt".
        using (StreamWriter outputFile = new StreamWriter(Path.Combine(docPath, "WriteTextAsync.txt")))
        {
            await outputFile.WriteAsync("This is a sentence.");
        }
    }
    }
    // The example creates a file named "WriteTextAsync.txt" with the following contents:
    // This is a sentence.

### How to: Read and write to a newly created data file summary

The System.IO.BinaryWriter and System.IO.BinaryReader classes are used for writing and reading data other than character strings.

    using System;
    using System.IO;

    class MyStream
    {
    private const string FILE_NAME = "Test.data";

    public static void Main()
    {
        if (File.Exists(FILE_NAME))
        {
            Console.WriteLine($"{FILE_NAME} already exists!");
            return;
        }

        using (FileStream fs = new FileStream(FILE_NAME, FileMode.CreateNew))
        {
            using (BinaryWriter w = new BinaryWriter(fs))
            {
                for (int i = 0; i < 11; i++)
                {
                    w.Write(i);
                }
            }
        }

        using (FileStream fs = new FileStream(FILE_NAME, FileMode.Open, FileAccess.Read))
        {
            using (BinaryReader r = new BinaryReader(fs))
            {
                for (int i = 0; i < 11; i++)
                {
                    Console.WriteLine(r.ReadInt32());
                }
            }
        }
    }
    }

    // The example creates a file named "Test.data" and writes the integers 0 through 10 to it in binary format.
    // It then writes the contents of Test.data to the console with each integer on a separate line.