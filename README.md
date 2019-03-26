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