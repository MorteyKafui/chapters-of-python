# CHAPTER 1

## Variables

A variables is like a container that holds values.
They can also be referred to as identifiers or reference to a value in memory.
An example of how to declare a variable in **_Python_** is this `username = "Bob"`. Here **_username_** is the variable or identifier to the value **_Bob_** in the computer's memory.
This means that the variable or identifier **_username_** serves as a reference or pointer to the value **_Bob_** in memory.
Another example is `age = 20`. Here the **_age_** identifier is a pointer to the value **_20_** in the computer's memory.
There are some rules in naming variables or identifiers in Python.
These are:

- The first character should be a letter or an underscore. Example `_user = "Tim"`. This is a valid way of declaring a variable.

- The rest of the characters can be any combination of letters, digits and underscore. Special characters like **@,%,$,#,&** are not allowed.

- Variables are case-sensitive. This means that when you declare a variable `user_score = 90` and another `USER_SCORE = 60`. They are not the same.

Some valid ways to declare variables are **_min_length, class_score, Username_** etc.
Also there are some special or reserved words in Python that cannot be used as variables names. Some of these words include **True, if, continue, global, from,assert, lambada, try, raise, import** etc
You can see all the reserved **_keywords_** in Python by using the _help_ function like this: `print(help("keywords"))`. This will display all the reserved words in Python.

There are other built-in function names like **_all, any, print, sum, max, min_** which cannot be used as variables names. To view the built-in names, you can type this type code `print(dir(__builtins__))`. Don't worry if you don't some of these codes now.

Any variable can be made to refer to another value; that is why it is called a variable. Example, when I declare a variable `user_age = 35`, I can reassign another variable to `user_age` variable like `bob_age = user_age`. Both variables will point to the same value and the same _id_. In Python both the `user_age` variable and the `bob_age` variable point to the same object, which is the `str` object. This is why Python is called a dynamically typed language. A variable in Python can be associated with any type of object, and it can later be rebound/reassigned to any other type of object. To see the type of the object that a variable is currently referring to, we can use the type function: `print(type(varialbe_name))`.
In Python, it is a convention to indicate that a variable is constant which means its value isn't supposed change by writting the variable name in capital or uppercase letters. Example, `MAX_LENGTH = 20`. Actually, this variable name can be changed or reassigned to a different object. So it is just a convention in the Python community.

> NB: In Python, variables are just names that refer (or point) to objects; the actual data is contained in the objects. So, objects are chunks of memory that store the actual values, and variables are names that link to objects by storing the memory address or location of the object. Some examples of objects are int, str, list, tuple, dict, set etc.

## Python Data Types

A data type represents specific/possible set of values and operations that can be performed on those values. The data types that are predefined in Python are built-in data types. The available data types in Python are:

- Integer(int): Represents whole numbers without a fractional part. Used for counting or indexing.

```python
age = 25
print(type(age))
```

- float(float): Represents real numbers with a fractional part. Used for measurements and continuous quantities.

```python
temperature = 36.6
print(type(temperature))
```

- complex(complex): Represents complex numbers with a real and an imaginary part. Used in advanced mathematical computations.

```python
complex_num = 1 + 2j
print(type(complex_num))
```

- String(str): Represents text and is enclosed in single, double, or triple quotes. Used for storing and manipulating text.

```python
greeting = "Hello, world!"
print(type(greeting))
```

- Boolean(bool): Represents one of two values: True or False. Used for conditional testing and logical operations.

```python
is_active = True
print(type(is_active))
```

- List(list): An ordered, mutable collection of items, which can be of different types. Used for storing sequences of items.

```python
fruits = ["apple", "banana", "cherry"]
print(type(fruits))
```

- Tuple(tuple): An ordered, immutable collection of items. Used for grouping related items that shouldn't be changed.

```python
coordinates = (10.0, 20.0)
print(type(coordinates))
```

- Dictionary(dict): A collection of key-value pairs, where keys are unique. Used for fast lookups and flexible data storage.

```python
student = {"name": "John", "age": 20, "grade": "A"}
print(type(student))
```

- Set(set): An unordered collection of unique items. Used for membership testing and eliminating duplicate entries.

```python
unique_numbers = {1, 2, 3, 4, 5}
print(type(unique_numbers))
```

- Fronzensets(frozenset): An immutable version of a set. Used for creating sets that cannot be changed after creation.

```python
immutable_set = frozenset([1, 2, 3, 4, 5])
print(type(immutable_set))
```

- NonType(None): Represents the absence of a value or a null value. Used to signify that a variable has no value.

```python
value = None
print(type(value))
```

Other data types you might come across are:

- Bytes(bytes): Represents immutable sequences of bytes. Used for binary data, such as files or network packets.

```python
byte_data = b"Hello"
print(type(byte_data))
```

- Bytearray(bytearray): Represents mutable sequences of bytes. Used for binary data that needs to be modified.

```python
byte_array = bytearray(5)
print(type(byte_array))
```

More on the collecion types like lists, tuples, dictionaries, sets and fronzensets in later videos.

## Objects

Everything in Python is an _object_. Any of the types we've looked at early on is an object. Fuctions, classes and modules are also objects in Python. NB: more on that later.

An Object is a chunk in the computer's memory used to store data.
Every object in Python has a **_type_**, a **_value_** and an **_id_**. The value of an object is the data that it contains, and the type of an object determines what kind of operations can be performed on the value. the id of an object is an integer that is unique and points to an object in memory. Each object has different **ids** which will never change during its lifetime or as far has it is still being referenced to by a variable. We can use the built-in `id()` function to get the id of an object in memory.

## Operators

An operator is a symbol or a word that specifies an operation to be performed. Examples are `+, **, is, //, >>, and, ==, <=` etc.

- Arithmetic Operators

  - Addition(+): Adds two numbers

  ```python
  a = 10
  b = 20
  c = a + b
  print(c) # c = 30
  ```

  - Subtraction(-): Subtracts the right-hand operand from the left-hand operand.

  ```python
  a = 40
  b = 20
  c = a - b
  print(c) # c = 20
  ```

  - Multiplication(\*): Multiplies two numbers.

  ```python
  a = 10
  b = 20
  c = a * b
  print(c) # c = 200
  ```

  - Division(/): Divides the left-hand operand by the right-hand operand.

  ```python
  a = 100
  b = 20
  c = a / b
  print(c) # c = 5
  ```

  - Modulus(%): Returns the remainder of dividing the left-hand operand by the right-hand operand.

  ```python
  a = 100
  b = 20
  c = a % b
  print(c) # c = 0
  ```

  - Exponentiation(\*\*): Raises the left-hand operand to the power of the right-hand operand.

  ```python
  a = 10
  b = 2
  c = a ** b
  print(c) # c = 100
  ```

  - Floor Division(//): Divides the left-hand operand by the right-hand operand and returns the largest integer less than or equal to the result.

  ```python
  a = 5
  b = 3
  c = a // b
  print(c) # c = 1
  ```

- Comparison Operators

  - Equal(==): Returns True if the operands are equal.

  ```python
  a = 5
  b = 3
  c = a == b
  print(c) # False
  ```

  - Not Equal(!=): Returns True if the operands are not equal.

  ```python
  a = 5
  b = 3
  c = a != b
  print(c) # True
  ```

  - Greater than(>): Returns True if the left-hand operand is greater than the right-hand operand.

  ```python
  a = 5
  b = 3
  c = a > b
  print(c) # True
  ```

  - Less than(<): Returns True if the left-hand operand is less than the right-hand operand.

  ```python
  a = 5
  b = 3
  c = a < b
  print(c) # False
  ```

  - Greater than or equal to(>=): Returns True if the left-hand operand is greater than or equal to the right-hand operand.

    ```python
    a = 5
    b = 3
    c = a > b
    print(c) # False
    ```

  - Less than or equal to(<=): Returns True if the left-hand operand is greater than or equal to the right-hand operand.

  ```python
  a = 5
  b = 3
  c = a <= b
  print(c) # False
  ```

- Logical Operators

  - and: Returns True if both operands are true

  ```python
  print(True and True) # True
  print(True and False) # False
  ```

  - or: Returns True if at least one of the operands is true

  ```python
  print(True or True) # True
  print(True or False) # True
  ```

  - not: Returns True if the operand is false

  ```python
  print(not True) # False
  print(not False) # True
  ```

  - not: Returns True if the operand is false

  ```python
  print(True or True) # True
  print(True or False) # True
  ```

- Assignment Operators

  - " = ": Assigns the value of the right-hand operand to the left-hand operand.

  ```python
  username = "Bob"
  age = 30
  ```

  - " += ": Adds the right-hand operand to the left-hand operand and assigns the result to the left-hand operand.

  ```python
  age = 10
  age += 20 # equivalent to age = age + 20
  ```

  - " -= ": Subtracts the right-hand operand from the left-hand operand and assigns the result to the left-hand operand.

  ```python
  age = 30
  age -= 20 # equivalent to age = age - 20
  ```

  - " \*= ": Multiplies the left-hand operand by the right-hand operand and assigns the result to the left-hand operand.

  ```python
  age = 3
  age *= 2 # equivalent to age = age * 2
  ```

  - " /= ": Divides the left-hand operand by the right-hand operand and assigns the result to the left-hand operand.

  ```python
  age = 30
  age /= 2 # equivalent to age = age / 2
  ```

  - " %= ": Takes the modulus of the left-hand operand with the right-hand operand and assigns the result to the left-hand operand.

  ```python
  age = 30
  age %= 2 # equivalent to age = age % 2
  ```

  - " //= ": Performs floor division on the left-hand operand with the right-hand operand and assigns the result to the left-hand operand.

  ```python
  age = 30
  age //= 2 # equivalent to age = age // 2
  ```

  - " \*\*= ": Performs floor division on the left-hand operand with the right-hand operand and assigns the result to the left-hand operand.

  ```python
  age = 30
  age **= 2 # equivalent to age = age ** 2
  ```

- Membership Operators

  - in: Returns True if the specified value is found in the sequence.

  ```python
  scores = [50, 79, 50]
  score = 50 in scores
  print(score) # True
  ```

  - not in: Returns True if the specified value is not found in the sequence.

  ```python
  scores = [50, 79, 50]
  score = 50 not in scores
  print(score) # False
  ```

- Identity Operators

  - is: Returns True if the operands refer to the same object.

  ```python
  bob_score = 60
  alice_score = bob_score
  print(alice_score is bob_score)
  print(bob_score is alice_score)
  ```

  - is not: Returns True if the operands do not refer to the same object.

  ```python
  bob_score = 60
  alice_score = bob_score
  print(alice_score is not bob_score)
  print(bob_score is not alice_score)
  ```

- Bitwise Operators
  - AND(&)
  - OR(|)
  - NOT(~)

## Type Conversion

The process of converting a value of one type to another type is called type conversion. There are two kinds:

- Implicit type conversion (Coercion)
- Explicit type conversion (Casting)

Implicit type conversion is done automatically by the interpreter when evaluating expressions of mixed types. Example `2 * 5.5`, the interpreter will convert integer 2 to the floating point
equivalent 2.0, and then both float operands will be multiplied, and the result will be a float.

Explicit type conversion is performed by writing the required type name followed by the value to be converted inside parentheses. Example `"10" + 60` will require explicit type conversion which is `int("10") + 60`.

## Printing Output

In Python, we use the `input` function to get input from the console and `print` function to display the output on the console.
When we use the print function to display multiple items, all the items are separated by a single space in the output. If we want to change this default behavior and want the items to be separated by something else, then we can specify a separator by adding a `sep` parameter at the end of the print call. Example

```python
day = 30
month = 10
year = 2024
print(day, month, year, sep = "/")
print(day, month, year, sep = "-")
```

From the output of our programs, we can see that every print call ends with a newline. This means that after printing everything, the cursor automatically moves to the next line. Thus, the output of the next print call starts with a fresh line. If we want the print call to end with something else instead of a newline, we can specify the `end` parameter. Example:

```python
print('Hello Python', end='---')
print('Python is easy', end=' ')
print('Python is interesting!', end='')
```

## Getting User Input

Most of the time, we have to write programs that interact with the user and behave differently depending on the user's response. To write such interactive programs, we should know how to get input from the user and use it in our program.

The built-in function `input()` can be used to get keyboard input from the user. When the `input()` function executes, the program is paused, and the user is expected to enter some text on the screen. Example:

```python
username = print('Enter user name : ', end='')
print('You entered', username)

```

When you execute this code, first, the message of the print call is displayed on the screen. After this, the input function is called; this call pauses the program, and the interpreter waits for the user to enter some text. The user types the input and ends the input by pressing the Enter key, and after this, the program execution continues. The input function returns the entered text as a string, which means that a string object is created. To use this string in our program, we have to assign it to a variable. In our program, we have assigned the string to a variable named username. After this, we used the variable username in a print function call.

## Comments

A comment is a piece of text that is inserted in between the code to explain the purpose of your code to other programmers or to yourself when you revisit the code. Code that is properly documented with comments makes the program more readable and understandable, and so it is easier to maintain and update. Comments are written only for human readers; they are ignored by the interpreter, so they have no effect on the execution of the program. In Python, a comment starts with a hash sign **(#)** and lasts till the
end of the current line. Any text after the **#** sign till the end of the line will not be executed. The interpreter just ignores it. A comment can be written on a new line or after a statement on the same line. If you need to write a multi-line comment (block comment), then you
have to precede each line with the **#** sign.

```python
#print("hello world) this is a comment and it won't be executed
print('Comment')
```

## Indentation In Python

Indentation is the whitespace (spaces or tabs) that is present before the beginning of a code line. In most of the languages, indentation is done just to increase the readability, but in Python, it is very important. Python forces programmers to structure their code through indenting. So, indentation is not a matter of style, but a part of syntax in Python. Indentation of each line matters; wrong indentation can result in either an indentation error or incorrect behavior of your program.

## Mutable and Immutable Types

We know that each object has a type, an id, and a value. The type and id of an object remain the same throughout the program; they cannot be changed. Whether the contained value can be changed or not depends on the mutability of the object. Python types can be categorized as either mutable or immutable depending on whether the value of an object of that type can be changed or not. If a type is immutable, the value inside an object of that type cannot be changed. You can never overwrite the value of an immutable object. If a type is mutable, then the value contained inside the object of that type can be changed at run time.

- Mutable types

  - list
  - set
  - dict

- Immutable types
  - bool
  - int
  - float
  - str
  - tuple
  - fronzenset

Mutable types support operations that can change the value inside the object at run time, while immutable types do not provide any operation that can change the value inside the object. The state of an immutable object is fixed at the time of creation and cannot be modified later.

You need to keep in mind that mutability has nothing to do with the variable names. Let us try to understand this. Suppose the variable name x refers to a mutable object, and the name a refers to an immutable object.

The object to which x is referring is a mutable object, so the value inside it can be changed. We generally say that it can be changed inplace. The object to which a is referring is an immutable object, so it will remain as it is throughout its lifetime. You cannot overwrite it; it cannot be changed in-place. The variable referencing any object can always be reassigned to a different object; we can make x, or a refer to a different object. So, mutability is associated with types and objects, not with variables.

You need to clearly understand the difference between the terms rebinding a variable and mutating an object. Rebinding a variable means making a variable refer to a different object, and mutating an object means making in-place changes in that object. Only mutable objects can be mutated.

## Functions and Methods

A function is a reusable piece of code with a name, and it can perform certain operations for you. You can give it some values called arguments; it performs some work for you, and it might give you a value back. The built-in functions are the functions that are already written for us and are always available, so we can easily use them.

We have already used some built-in functions, like `print, input,type,` and `id`. We know that to call them, we need to write their name followed by parentheses, which can include some arguments. Arguments are values that provide some information to the function for performing its work. If the function doesn't need any arguments, then the parentheses remain empty.

A method is like a function, but it is specific to a type, and we access it by using a dot. To call a method, we write the variable name or a literal followed by a dot, then the method name, and then the parentheses, which can include arguments. Examples:

```python
message = 'hello'
message.upper()
list1 = [1, 2, 3, 4, 5]
list1.append(10)

```

Here, we are calling the method upper on a string literal, and we are calling the method append on a variable named list1 that refers to a list object.

Functions are not specific to any type, so they are called independently without the dot syntax. You can think of functions as generic operations that can work with multiple types.

For example, the built-in function len can be used to find the length of a string, list, or a dictionary. Methods are type specific operations that are attached to types and can act on an object of a specific type only. For example, the method upper can act only on an object of type str, and the method append can act only on an object of type list.

To know about the methods available for a data type, just type `dir(typename)` on the interactive prompt, and it will show you all the methods available for that type.

```python
print(dir(str))
print(dir(int))
print(dir(list))
```

There will be lots of methods with leading and trailing underscores, and these methods represent the implementation details of the type and help in customization. The methods towards the end are the ones without any underscore, and these are the methods that we will be mostly using.

This command shows you the names of methods. If you want to know more about a particular method, you can use help. On the interactive prompt, write help, then inside parentheses, write typename followed by a dot and then the method name.

```python
print(help(list.extend()))
```

These functions `dir()` and `help()` accept both the type name or a variable name. So, suppose you have a variable s referring to a string object, you can use dir and help on s also. If you write `help(typename)` then it will show you the description of all the
methods.

## Importing

There are many predefined functions in the standard library that we can use in our program, but unlike built-in functions, these functions are not automatically available in our program. These functions are organized in modules (Python files), and we have to import them to make them available in our program. For example, the `math` module contains many mathematical functions. The `random` module provides functions for randomization.

```python
from math import sqrt, trunc
x = 34
y = 23.4
print(sqrt(34))
print(trunc(23.4))
```

If you import a module by writing import _modulename_, then all the names in that module can be used in your program, but they have to be preceded by the module name and a dot.

```python
import math
x = 34
y = 23.4
print(math.sqrt(34))
print(math.trunc(23.4))
```

We can import modules from the rich standard library and make use of lots of pre-existing functionality, and that is why the term 'batteries included' is used for Python. You can see a list of standard library modules in the official Python documentation, and to know more about a module, import it on the shell and use help on it.

```python
import math
print(help(math))

```

To see all the available names in a module, you can use the `dir()` function after importing it.

```python
import math

print(help(math))
```

To get help on a specific name from the module, use help on that name.

```python
import math
print(help(math.floor))
```

## The End
