# CHAPTER 8 - Functions

A function is a named block of code that performs a specific task.

So basically, we have two types of functions in Python; built-in functions and user defined functions. Built-in functions are some general-purpose functions that are already written, we just use them in our program. User defined functions are written by programmers to suit specific needs of their program.

The main advantage of using functions is code reusability; they make the code reusable and reduce code duplication.

In this process, we have two main things – defining a function and
calling a function. Writing the block of code and naming it, is called defining the function, and invoking the block of code by its name is called a function call.

## Function Definition

The definition of a function creates the function while the function call runs the code inside the function.
A function in Python is defined by a `def` statement.
Syntax:

```python
def function_name(param1, param2, ...):
  statemanet1
  statemanet1
  statemanet1

```

The function definition consists of two parts - the header line and the function body. The header line begins with the keyword `def`, followed by an identifier, which is the name of the function, and then a pair of parentheses, which may enclose some identifiers separated by commas. These identifiers are parameter names. Parameters are input to the function; they enable us to pass different values to the function. The whole header line ends with a colon. This header line is also known as the function’s signature. If the function does not have parameters, it must still include the empty parentheses. Here is the syntax of a function definition for a function that does not have any parameters:

```python
def function_name():
  statemanet1
  statemanet1
  statemanet1

```

Following the header line is the body of the function. The function
body consists of one or more Python statements; it contains the full code of the function. All the statements inside the function body should be indented by the same amount from the header line. It is best to follow the standard of _4 spaces_. The code block of the function ends with the first non-indented statement.

The name of the function can be any valid Python identifier, they
follow the same rules that we saw for naming identifiers. The name
of the function should be descriptive, and conventionally, it is in all lower case with words separated by underscores.

```python
def greet():
  print("Hello from Python")
```

This function `greet1` takes one parameter, which is placed inside the parentheses. Here also, the function body has only one statement. We have used the parameter named name inside the function body.

```python
def greet1(name):
  print("Hello ", name)
```

This function named calculate takes two parameters, `a` and `b`.

```python
def calculate(a, b):
  print(a + b)
  print(a - b)
  print(a * b)
```

When we run the python file, the `def` statements are executed and they create 3 function objects. Everything in Python is an object, and so are functions. The def statement is an executable statement that creates a new function object and assigns that object to the
function’s name.
You can check this: `print(type(function_name))`, outputs `<class function>`
We can see the id of the function object. `print(id(function_name))`

# Function call

The statements inside the function body are not executed when the
`def` statement executes. To execute the statements inside the
function body, we have to call the function. So, now let us see how to call a function. If the function has no parameters, then it is called by appending empty parentheses to the function name. The function greet that we have written has no parameters, so it called like this: `greet()`
So, a function call instructs the interpreter to execute the body of the function; it is also called **function invocation**. A function is defined once and can be called any number of times in our program.

Now, let us see how we can call the function greet1. From the
definition, we can see that it takes one parameter. This means that
this function needs some input, when it is called. So, while calling the function we will send a value to this function.
`greet1('Sam')`

The string that we have provided here inside the parentheses in the
call will be assigned to the parameter name that we have in the
function definition. When we run the program, this function call will call the function greet1 with parameter name referring to 'Sam' and so Hello Sam will be printed. If you do not send any argument and leave the parentheses empty, then there will be an error. `greet1() # gives error`

We can call the function `greet1()` with any other value also.
`greet1('Bob')` Now the parameter refers to the string 'Bob', so Hello Bob will be printed in the output. We can see that parameters make our function flexible. The same function code can be executed for different values.

## Flow of control

A function definition does not alter the flow of control, but a function call does. When a function call is encountered, the control is transferred to that function. After all the statements inside the function’s body are executed, control returns back to the place where the function was called and the program flow resumes at the point just after the function call.
The code block of a function can include calls to other functions, so while executing a function code block, the control might have to jump to another function. Python keeps track of all these calls, and knows where to return once a function code block has finished executing.

## Parameters and Arguments

We have seen that when we call a function that has parameters, we
need to send some values for those parameters; these values are
called arguments. Parameters are the names inside the parentheses
of the header of function definition and arguments are the values
that we supply in the function call. The arguments provided during
the function call are assigned to the corresponding parameters
present in the function definition. The function body uses the
argument values by referencing the corresponding parameter name.

## Local Variables

We can define variables inside the function body. These variables are considered local to the function.

```python
def summation(a, b):
  s = 0
  for i in range(a, b + 1):
      s += i
  print(s)

```

In this function, the variable s is a local variable. It exists only while the function is running and is destroyed when the function finishes executing. If you try to access this variable outside the function, you will get an error. The variable i in the for loop is also a local variable. Parameters in the function definition are like any other variable created inside the function definition, except that they are assigned automatically. Thus, the parameters of a function are also local variables of the function.

The variables defined inside the function, along with the parameters, comprise all the local variables of the function. All these names come into existence when the function is called and are destroyed when the function finishes execution. The local variables are visible only inside the function, they cannot be used anywhere else in the program. If you try to access any local variable outside the function then the interpreter will complain. This also means that you can use the same variable name inside different functions, without any clash.

```python
def add(a, b):
  s = a + b
  print(s)
```

Using the name s in this function add is acceptable. The name s is
different for both the functions summation and add, one is visible
inside the summation function, and the other s is visible inside the add function. A variable that is created outside any function is a global variable.

## return statement

If the function wants to return some data to the caller, then it needs to use the `return` statement.

```python
def simple_interest(p, r, t):
  si = (p * r * t) / 100
  print(f'Simple interest is {si}')

  return si

principal = 2000
rate = 5
time = 4
simple_interest(principal, rate, time)
```

Here, we have a function named simple_interest that takes in
principal, rate, and time, calculates the simple interest, and prints it. The parameters are p, r, and t, and inside the function, we have a local variable named si which is used to store the simple interest. The value of this variable si is printed inside the function.

Instead of printing `si`, we return the value of `si` from the function. For this, we have written the return keyword followed by the name `si`.

`return` keyword is written, followed by an optional expression.
When this statement is encountered inside a function definition, the function’s execution stops immediately, and the control is returned to the caller. The value of the expression is used as the return value which is returned to the caller.
Syntax: `return [expression]`

The expression can be any literal value like `number`, `string` or `Boolean` value `True` or `False`, it can be any variable as we have in our simple interest example, or it can be any expression combining all of these, or you can even return `None`.

It is optional to specify the expression in the return statement. You can write a return statement without any expression. The return
statement without any expression is generally used to stop the
execution of the function when a condition is checked.

In Python, a `return` statement without any expression is the same
as `return` statement with a value of `None`. When you write return
without any expression, Python returns `None`.

## Returning Multiple Values

A function returns exactly one value and that value can be of any
type; it can be an int, float, list, tuple or a dictionary. When you want to return multiple values from a function, you can pack those values into a single data structure like list, set, or tuple and then return that data structure from the function. So technically, you will be returning only one entity, but you will be able to return multiple values in that one entity.

```python
def func(a, b):
  s = a + b
  d = a - b
  p = a * b
  return (s, d, p)

t = func(4, 5) # t is a tuple of the returned values (9, -1, 20)

sum, difference, product = func(4, 5) # unpacking the returned values from the function
print(t, sum, difference, product) #  9 -1 20
```

## Pass by assignment

We have seen that when a function call executes, the arguments are
assigned to the corresponding parameter names. This assignment
happens implicitly, before the function body executes, so we can say arguments are passed by assignment. Assignment in Python means
object reference (or binding a name to an object), so we can also say that arguments are passed by object reference. Therefore, arguments passing mechanism in Python is called pass by assignment or pass by object reference.

In Python, every variable is just a reference to an object that contains the actual data. The variable does not store the data directly, it only has information about where the object that contains the data is located in memory. You can think that a variable just contains the location of the object and it is this location that is passed to the function. The parameter name gets this location and so it also starts referring to the same object. So, we can see that the object is not passed, no copy of the object(data) is made, instead only reference to the object is passed (location of object is copied). This is why the mechanism is named pass by object reference (or call by object reference). The same object is shared by both the argument variable and the parameter and so the mechanism is also sometimes called call by sharing.

## Assignment Inside function rebounds the parameter name

When a variable is sent as argument, initially the argument and
parameter share the object, i.e. they refer to the same object, but as soon as the parameter name is reassigned, this sharing ends. So, if we assign to a parameter name inside the function, it is rebound which means that it starts referring to some other object and the connection to the original object is lost.

## Immutables vs Mutable as arguments

We know that the function gets access to the object through the
reference that is passed; if the referred object is mutable, then the function can make in-place changes in it which will be visible to the caller.
The conclusion is that when a variable bound to an immutable object
is passed as argument, the changes do not propagate to the caller in any way. When a variable to a mutable object is passed as argument, the changes can propagate to the caller if the object can be changed in-place.

## Default Arguments

If there is some argument value that would be used most of the
times while calling the function, we can make it a default value for the parameter. This default value will automatically be used as the argument, if the user of the function does not provide the
corresponding argument for that parameter. These default values are
called default arguments. These values are provided in the header of the function definition.

```python
def func(a, b=5):
  print(a, b)
```

## Positional and Keyword Arguments

- Positional Arguments
  We have seen that the argument values that we supply in the function call are matched to parameter names by position, from left to right. For example, in the following code, the first argument is matched to first parameter, second argument is
  matched to second parameter and third argument is matched to third parameter.

  ```python
  def func(name, title, salary):
    print(f'{name} is a {title} and gets {salary}')
    func('Nick', 'manager', 5000)
  ```

  The interpreter matches the arguments based on their position.
  Arguments matched by their position are called positional arguments.

- Keyword Arguments
  In Python, there is an alternative way to specify arguments in the function call.
  `func(name='Nick', title='manager', salary=5000)`
  In this syntax, we write the parameter name, then equal sign, and then the argument value that we want to assign to the parameter. We clearly specify which value is for which parameter and so now matching of argument and parameter is explicit. If we specify a name in the call that does not match any of parameters in the definition then there will be an error. When we specify parameter names in the call, the arguments are identified by the parameter name and not by position, so the order of arguments does not matter. We can write the function call with different orders of parameter=argument pairs. `func(title='manager' salary=5000, name='Nick') func(title='manager', name='Nick', salary=5000)`

The arguments that are matched by position are called positional
arguments and the arguments that are matched by parameter name
are called keyword arguments (or named arguments). Thus, a
positional argument is an argument that is assigned to a parameter
based on its position in the argument list while a keyword argument
is assigned to a parameter based on the parameter name specified
along with the argument. You can mix positional and keyword arguments in a single call. When you do this, all the positional arguments have to appear before the keyword arguments.
`func('Nick', salary=5000, title='manager')
 func('Nick', 'manager', salary=5000)`

## Unpacking arguments

When an argument in a function call is preceded by a single `asterisk (*)`, it means that the argument is a list, tuple, set or string. Such an argument will be unpacked and the contained values will be sent to the function as positional arguments.

When an argument in a function call is preceded by a double `asterisk (**)`, it means that the argument is a dictionary. The dictionary will be unpacked and its key value pairs will be used to provide keyword arguments to the function.

## Variable number of positional arguments

to gather all the variable number of arguments, you just need to
specify a parameter with an _asterisk_ in front of it. You can give this parameter any other name of your choice, but conventionally it is named `args`.

```python
def func(num1,num2, *args):
  pass
func(1,2)
func(1,2,3,4,5,6,7)
```

When you need to write a function definition, but you don’t know
how many arguments it will receive when it will be called, you can
use this `*args` parameter. You can combine this parameter with
other parameters. args. This way we can collect all the extra arguments using `*args`. So, we can use other parameters with *args, but all those parameters should come before *args.

## Variable number of keyword arguments

We can define a function in such a way that it can accept any number of keyword arguments.

Previously, we learned that we could gather additional positional arguments using a single parameter by placing an asterisk before the parameter name. Similarly, to collect additional keyword arguments, we need to prefix the parameter name with two asterisks. While extra positional arguments were collected in a tuple, extra keyword arguments will be gathered in a _dictionary_. We have seen that conventionally, the parameter that is used to collect positional arguments is named args. Similarly, by convention, the parameter that is used to collect keyword arguments is called _kwargs_. Therefore, in the function header, we generally write `*args` to collect positional arguments and `**kwargs` to collect keyword arguments.

```python
def func(**kwargs):
  for x, y in kwargs.items():
  print(x, y)
```

This is a simple function definition with \*\*kwargs in the header. This parameter will be used to collect a variable number of keyword
arguments. All those arguments will be collected in a dictionary
named _kwargs_ which we can use inside the function body. Inside
the function, we are just iterating over the kwargs dictionary and
printing its keys and values.

For unpacking, we used a single or a double asterisk before the
argument name in the function call, for packing we used a single or a double asterisk before the parameter name in the function definition.

By specifying `*` before argument name in the function call, we can
unpack a list, tuple or string to get positional arguments. By
specifying `**` before argument name in the function call, we can
unpack a dictionary to get keywords arguments.

## Attributes of a function

Functions are objects in Python, and so they have different attributes attached to them. We can use the dir function to get all the attributes.

```python
def func(a, b, c=1, d=2):
  print(a, b, c, d)

dir(func) # [list of func atttibutes]
```

## Docstrings

When you use a built-in function, you want to know just what the
function does, what arguments it takes and what it returns. You are
not concerned about how the function does its job. Similarly, the
functions that you write might be used by some other users. They
will want to call your function, so they need to know information like its purpose, arguments, and return value. This is why it is good to provide documentation. Documentation for functions is done by providing documentation strings, which are in short called docstrings.

```python
def add(a, b):
''' Add the two numbers.
Input: two numbers
Return : sum
'''
  s = a + b
  return s
```

A docstring is a string literal placed just after the header line and before the function statements. It is usually enclosed in triple quotes so that it can span more than one line. It appears as a tooltip when you try to call the function. When you seek help on the function then also it appears. `help(add)`

## The End
