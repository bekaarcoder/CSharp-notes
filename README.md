# C# Notes

## Naming Conventions

- For local variables: Camel Case (int rollNumber)
- For constants: Pascal Case (const int MaxZoom = 5)

## Primitive Types

- Integral Numbers
  - Byte
  - Short
  - Int
  - Long

- Real Numbers
  - Float
  - Double
  - Decimal

- Character – char
- Boolean – bool

> Note – double is used as a default data type when using real numbers in C#.

- Declare a float `float number = 1.2f`
- Declare a decimal `decimal number = 1.2m`

**Overflowing** – Overflow happens when we perform an operation with a data type and the result of this operation exceeds the size of a storage for this datatype.
  ```c#
  byte number = 255;
  number = number + 1 //this will output 0
  ```

## Type Conversion

1. **Implicit Type Conversion**
  ```c#
  byte b = 1;
  int i = b;

  int i = 1;
  float f = i
  ```

2. **Explicit Type Conversion**
  ```c#
  int i = 1;
  byte b = i //won't compile, so we use explicit type conversion

  byte b = (byte)i;
  ```

3. **Non-Compatible Types**
  ```csharp
  string s = "1";
  int i = (int)s; //won't compile

  int i = convert.ToInt32(s);
  or
  int i = int.Parse(s);
  ```

## Non-Primitive Types

1. String
2. Array
3. Enum
4. Class

### Classes
Combines related variables (fields) and functions (methods).

**Declaring a class**
  ```csharp
  public class Person {
    public string Name;
    public void Introduce() {
      Console.WriteLine("Hi, my name is " + Name);
    }
  }
  ```

**Creating Objects**
  ```cs
  Person person = new Person();
  //or
  var person = new Person();
  person.Name = "John";
  person.Introduce(); //Hi, my name is John
  ```

### Arrays
An array is a data structure to store a collection of variables of the same type.

**Declaring an array**
```cs
int[] numbers = new int[3];
numbers[0] = 1;
numbers[1] = 2;
numbers[3] = 3;

//or directly use object initialization syntax
int[] numbers = new int[3] {1, 2, 3};
```

### Strings
A sequence of characters.

**Creating strings**
```cs
string name = "John";

//Using string concatenation
string name = firstName + " " + lastName;

//Using string format
string name = string.Format({0} {1}, firstName, lastName);

//Using string join
var numbers = new int[3] {1, 2, 3};
string list = string.Join(",", numbers); //1,2,3
```

**String Elements**
```cs
string name = "John";
char firstChar = name[0]; //J

name[0] = 'm'; //cannot be done as strings are immutable
```

> Strings are Immutable. Once you create them, you cannot change them.

**Escape Characters**

Char | Description
-----|----------
 \n | New Line
 \t | Tab
 \\ | Backslash
 \' | Single Quotation Mark
 \" | Double Quotation Mark

 **Verbatim Strings**
 ```cs
 string path = "c:\\projects\\csharp\\folder";
 //using verbatim strings
 string path = @"c:\projects\csharp\folder";
 ```

 ### Enums
 A set of name/value pairs (constants).
 ```cs
public enum ShippingMethod {
  RegularShipping = 1,
  RegisteredMail = 2,
  Express = 3
}

var method = ShippingMethod.Express;

//We can also specify the type for enum
public enum ShippingMethod : byte {

}
``` 

## Arrays

Represents a fixed number of variables of a particular type.

**Type of Arrays**

1. **Single Dimentional Arrays**
    ```cs
    var numbers = new int[5];
    var numbers = new int[5]{1, 2, 3, 4, 5};
    ```

2. **Multi Dimentional Array**
    - **Rectangular Array** - Number of columns for each rows are same.
        ```cs
        var matrix = new int[3, 5]; //3 rows and 5 columns
        var matrix = new int[3, 5]{
          {1, 2, 3, 4, 5},
          {6, 7, 8, 9, 10},
          {11, 12, 13, 14, 15}
        };
        ```
    - **Jagged Array** - Number of columns for each rows are different.
        ```cs
        var array = new int[3][];

        array[0] = new int[4];
        array[1] = new int[5];
        array[2] = new int[3];
        ```

## Array Properties and Methods

```cs
var numbers = new[] {3, 4, 5, 6, 7, 8, 9, 0};

//Length
Console.WriteLine(numbers.Length); // 8

//IndexOf()
var index = Array.IndexOf(numbers, 5)
Console.WriteLine(index); // 2

//Clear()
Array.Clear(numbers, 0, 2);

foreach(var n in numbers)
  Console.WriteLine(n); // {0, 0, 5, 6, 7, 8, 9, 0}

//Copy()
int[] another = new int[3];
Array.Copy(numbers, another, 3); // {3, 4, 5}

// Sort()
Array.Sort(numbers) // {0, 3, 4, 5, 6, 7, 8, 9}

//Reverse()
Array.Reverse(numbers) // {0, 9, 8, 7, 6, 5, 4, 3}
```

## Lists
List clas can be used to create a collection of different types like int, string, etc. It can be resized dynamically.

**Creating a List**

```cs
var numbers = new List<int>();
var numbers = new List<int>() {1, 2, 3, 4, 5};
```

**Lists Methods**

```cs
var numbers = new List<int>() {1, 2, 3};

numbers.Add(4); // {1, 2, 3, 4}
numbers.AddRange(new int[3] {5, 6, 7});

foreach(var number in numbers) {
  Console.WriteLine(number);
} // {1, 2, 3, 4, 5, 6, 7}

Console.WriteLine(numbers.Count); // 7
```

## Working With Strings

### Converting Strings to Numbers

```cs
string s = "1234";

int i = int.Parse(s);
int j = Convert.ToInt32(s);
```

### Converting Numbers to Strings

```cs
int i = 1234;

string s = i.ToString(i); // "1234"
string s = i.ToString("C"); // "$1,234.00", C is for Currency
string s = i.ToString("C0"); // "$1,234" , C0 removes digits after decimal. To use 1 decimal place, use "C1".
```

## Working With Files

**File** - provide static methods
**FileInfo** - provide instance methods

> Both provide methods for creating, copying, deleting, moving and opening of files.

**Directory** - provide static methods
**DirectoryInfo** - provide instance methods

**Path**

- GetDirectoryName()
- GetFileName()
- GetExtension()
- GetTempPath()

## Class
A building block of an application.

**Anatomy of a Class**

- Data (represented by fields)
- Behaviour (represented my methods/functions)

|Post                                                      |
|----------------------------------------------------------|
|Title: string<Br>Description: string<Br>DateTime: DateTime|
|Publish()<Br>Like()<Br>Comment(message)                   |

## Object
An instance of a class.

### Declaring Classes

```cs
public class Post {
  public string Title;

  public void Publish() {
    Console.WriteLine("Creating the post " + Title);
  }
}
```

### Creating And Using Objects

```cs
Post post = new Post();
//or
var post = new Post();

post.Title = "My first post";
post.Publish();
```

**Class Members**

- Instance: accessible from an object.
    ```cs
    var person = new Person();
    person.Introduce();
    ```
- Static: accessible from the class.
    ```cs
    Console.WriteLine("Hello");
    ```

## Constructor
A method that is called when an instance of a class is created. It has the same name as of the class name.

```cs
public class Customer {
  public Customer() {

  }
}
```

## Constructor Overloading
It is a technique of creating multiple constructors with a different set of parameters and the different numbers of parameters.

```cs
public class Customer {
  public Customer() {...}

  public Customer(string name) { ... }

  public Customer(int id , string name) { ... }
}
```

