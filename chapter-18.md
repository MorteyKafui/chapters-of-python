# CHAPTER 18 - Exception Handling

Exception handling code gives your program the ability to handle any failures or problems that occur during execution time.

## Types of Errors

- Syntax Errors
- Run time Errors
- Logical Errors

## Strategies to handle exceptions in your code

1. LBYL - Look Before You Leap
   In this approach, we use conditional checks to eliminate any possibility of error. Whenever we have to perform any error-prone operation, first, we make sure that all conditions are favorable for the execution of that operation. We check all the situations that can make the operation give errors and we do this by placing conditional checks in the form of `if` statements. When the conditions are favourable, then only we execute the operation. If there is any possibility of error, we do not execute the operation.

2. EAFP - Easier to Ask for Forgives than Persmission
   In this approach, we try to execute the code assuming that everything will work correctly, but if our assumption proves false and something goes wrong, we deal with it. Python supports this approach with the help of `try…except` statement.

   ```python
   try:
    print('Ratio of boys to girls is ', boys / girls)

   except ZeroDivisionError:
    print('No girls, Ratio not defined')
   ```

   > From these two approaches, EAFP is more Pythonic; it is commonly used by Python programmers, while LBYL is common in other languages like C, which don’t have any exception-handling mechanism.

## Error Handling by Python (Default exception handling)

There are many built-in classes in Python that are dedicated to errors. Here are some of them: `IndexError, NameError, AttributeError, ZeroDivisionError, ValueError, TypeError, ModuleNotFoundError, FileNotFoundError`

An exception is an instance of one of these classes. So, whenever a run time error occurs, the interpreter stops the normal control flow of the program and creates an instance of the appropriate class. For example, if there is an attempt to divide by zero, then the interpreter creates an instance of the `ZeroDivisionError` class. This is called exception object or simply exception and it contains information about the error that has occurred. After creating the exception object, the run time system starts searching for exception handling code in the program. If it finds the code to handle the particular type of exception that was created, then it executes that code and continues with the rest of the program. If it does not find a suitable exception handling code, then it terminates the program. This search for an appropriate exception handler for a raised exception is called _exception propagation_.

Python creates a stack of function calls during the program execution. This stack is made up of frames; there is a frame for each function call. When a function is called, a frame is pushed on the stack, and when a function returns, a frame is popped from the stack.

## Built-in Exceoptions: Python Exceptions Class Hierarchy

Exception classes in Python can be of two types: built-in classes or custom classes. Built-in classes are predefined in Python; they are also called standard exceptions. Custom exception classes are defined by the programmer for their special needs.

The built-in exception classes are organized in a hierarchy using inheritance. This inheritance structure of exception classes categorizes exceptions into different types. Python raises them in many different situations as we have seen, and mostly all the modules in the standard library also use these exceptions.

The class `BaseException` is the base class of all the built-in exception classes. From `BaseException`, four classes named `Exception, SystemExit, KeyboardInterrupt` and `GeneratorExit` are derived. All the remaining built-in exception classes are derived directly or indirectly from the `Exception` class. The figure shows some of the classes derived from `Exception` class; there are many other classes also. These classes are all present in `builtins` module, you can import this module and use `dir` function on it to see all the exception class
names.

```python
import builtins
dir(builtins)
help(builtins)
```

## Custom Exception Handling by using `try...except`

An exception that is raised can be caught and handled by the exception handling code. We have seen that if a raised exception is not caught, then the Python interpreter terminates the program and reports an error message and a traceback to the console. If you do not want the program to terminate abnormally, then you need to catch and handle the exception that is raised by Python. You need to write your error handling code using the `try` statement. `try `statement is a compound statement with different clauses, it can take one of these two forms.

```python
try:
  code1
  code2
  code3
except ExceptionA:
  code4
  code5
except ExceptionB:
  code6
  code7
else:
  code8
finally:
  code9
  code10
```

```python
try:
  code1
  code2
  code3

finally:
  code9
  code10
```

We have the keyword `try` followed by a colon, and inside the try block, we will have those statements that we think can cause exceptions. After that, we have the keyword `except` followed by an exception name and a block of statements. If an exception occurs at any statement inside the `try` block, then the interpreter stops executing the try block. The remaining statements in the `try` block are not executed, and the control jumps to the except clause. If the exception raised inside the `try` block matches the exception written in the `except` clause, then the code in the `except` block is executed, and after that, the control is transferred to the next statement after the whole `try…except` statement.

The `except` block is also known as the exception handler since it includes the code to handle the exception. If the raised exception does not match the exception mentioned in this `except` clause, then it is propagated up, and if it does not find any suitable handler, then the program is terminated. In any case, whether the exception matches or not, the remaining statements of the `try` block are skipped. They are never executed. So, that is why you should keep your `try` block as short as possible; it should contain only the error-prone code. It is not good to enclose your whole program or a big part of your program inside the `try` block. While writing the code, you must identify the statements that can cause exceptions.

```python
boys = int(input('Enter number of boys '))
girls = int(input('Enter number of girls '))
try:
  r = boys / girls
  print(f'Ratio of boys to girls is {r}')

except ZeroDivisionError:
  print('No girls, Ratio not defined')
  total = boys + girls

print(f'Total number of students = {total}')
```

Now, when the `ZeroDivisonError` occurred, the `except` block was executed, and after that, the program continued normally. So, while writing the code, if you suspect that some lines of code can raise exceptions then you should put them inside `try` blocks and write appropriate `except` handlers.

## Catching multiple exceptions using multiple except handlers and single except handler

```python
statement1
statement2
statement3
statement4
statement5
try:
  statement6
  statement7
  statement8
except ValueError:
  statementX
  statementY
  statement9
  statement10
  statement11
  statement12

```

## Guaranteed execution of finally block

Before seeing the details of the finally block, let us first understand why we need one. Suppose you have opened a database connection, and you are performing some operations on that database. After these operations, finally the connection has to be closed, which is very important otherwise it can lead to loss of data and resource leakage problems.

The `finally` block is placed after all the except blocks and is always executed before leaving the `try` block. It is executed irrespective of whether an exception occurs or not and whether it is handled or not. So, the code in the `finally` block is executed in all the three situations that we saw. When no exception occurs in the `try` block, the finally block will be executed after the execution of the `try` block. When an exception occurs in the `try` block and is handled by one of the except blocks, then the `finally` block is executed after executing the corresponding except block. When an exception occurs but is not handled and is propagated up, then the `finally` block is executed before the exception propagation occurs. The `finally` block is also executed if the control leaves the try block because of a break or a return statement. So, the `finally` block is the best place for our Close Connection code. When we have some external resources that were allocated by the program and were being used in the `try` block, and we want to ensure that they are properly released, then we can place the code for releasing them in the `finally` block, since it is the block which is guaranteed to be executed in any case. So, the finally block is used for placing any final processing code that needs to be executed under all circumstances. The final processing code could include closing files, closing database or network connections, logging out the user, releasing locks, or writing final log messages. The `finally` block ensures proper termination of any processes that are running. You can place the `finally `clause after all the except blocks or you can have a `try` statement with only a `try` clause and a `finally` clause.

The `try…finally` form is useful when you want your cleanup code to be run, even when you do not handle any exceptions that occur and let them propagate up. Any exceptions that occur in the `try` block will be propagated up since we do not have any `except` block in this form, but the cleanup code will run before the propagation of exception. The purpose of this form of `try` statement is not exception handling. It is there to ensure execution of the clean-up code.

## `else` Block

The `try` statement can have an optional `else` clause. The `else` block should be placed after all the `except` blocks. It executes only when the `try` block terminates normally. It will not be executed if any exception is raised in `try` block or if the `try` block terminates due to a `break`, `continue` or `return` statement. If `finally` block is present in the `try `statement, then the `else` block should be placed before the `finally` block.

If you want to write the `else` clause in your `try` statement, then there should be at least one `except` block present. You cannot use it in the `try…finally` form we saw in the previous section. The following `try` statement will give syntax error because there is no `except` block, and we have written an `else` clause.

```python
try:
  …………
else:
  …………
finally:
  …………
```

The `else` block is executed only if no exception occurs during the execution of the `try` block.

When no exception occurs in the `try` block, the three statements inside the `try` block are executed, then the `else` block executes, and then the `finally` block executes. The second situation could be when an exception occurs in the `try` block and is handled in one of the `except` blocks. For example, suppose `ValueError` is raised at `statement2`. In this case, first `statement1` executes, then the `try` block is suspended due to `ValueError` at `statement2`, and the corresponding `except` block executes. The `else` block will not execute in this case as it executes only when there is no exception in the `try` block. After the `except` block, the `finally` block executes, and then control comes out of the `try` statement, and the statements 6 and 7 are executed. The third situation could be when an exception is raised in the `try` block but is not handled here. For example, suppose an `ArithmeticError` occurs at `statement2`. In this case, first the `statement1` executes, and then the `try` block is terminated due to an exception at `statement2`. `ArithmeticError` cannot be handled here so it will be propagated up. The else block will not be executed, the `finally` block executes before propagation of exception and the control in this case will not reach to `statement 6`, it will be transferred to the previously entered `try` block. So, we saw that the `else` block executes only in the case when no exception is raised in `try` block, if an exception is raised whether handled or not, the `else` block does not execute.

## How to get exception details

We know that when an exception is raised, an exception object is created, which contains information associated with the exception. Usually, it contains an error message, but it might contain other information. This information can be useful in handling the exception. To retrieve this information, you will need a reference to the exception object. You can get access to this object by using the `as` keyword in the `except` clause. In the following `try` statement, we have used the as keyword with the identifier `e `in the first except clause. The identifier `e` will be a reference to the exception object that would be created when `LookUpError` exception occurs in the `try` block. By using this reference, you can access any of the attributes or methods of the raised exception object.

```python
try:
  statement1
  statement2
  statement3
except LookUpError as e:
  statementX
  statementY
except ValueError:
  statementA
  statementB
else:
  statement4
  statement5
finally:
  statementC
  statementD

```

When Python creates a new exception instance, it passes some arguments to the exception constructor, these arguments indicate information related to the error. The argument values that it provides to the constructor are stored in the attribute `args` which is actually a tuple. So, every exception instance has an attribute `args` which is a tuple, and it contains arguments that are passed when the exception object is created. Let us create some exception objects (instances of exception classes) and see the `args` attributes for them.

So, we can see that every exception instance has the `args` attribute which we can access in the `except` block if we get a reference to the instance using the `as` keyword. Another thing that is inherited by all classes is the string representation. String representation of an exception is provided in the `BaseException` class, so all other exception classes inherit it. When `str()` function is called on an instance of any exception class, we get the string representation.

## Nested `try` statements

Nesting of a `try`statement can happen in two ways: (i) when we write a `try` statement inside the `try` block of another `try` statement. (ii) when we have a function call inside a `try` block and inside that function’s definition, there is another try statement. We will see both of these in detail. First, let us see the first one, which has a try statement physically embedded inside another try block.

```python
try:
  statementA
  try:
    statementP
    statementQ
  except IndexError:
    statementR
  except ValueError as e:
    statementR
  else:
    code1
    code2
  finally:
    code3
else:
  ............
finally:
  .........

```

## Raising Exception

`raise` statement can be used to `raise` exceptions manually, which means that your code can explicitly `raise` exceptions. Before seeing the full syntax of the `raise` statement, let us see a simple example that uses `raise` statement.

```python
age = int(input('Enter age : '))

if age < 0 or age > 120:
raise ValueError
```

We have written the `raise` statement that consists of the `raise` keyword and the name of the exception. A `ValueError` exception will be raised when the value of age is less than 0 or greater than 120.

The effect of raising an exception using `raise` statement, is the same as that of any exception raised by Python. The normal flow stops and search for a matching except clause starts in the enclosing `try` statements. The exceptions raised by the `raise` statement can be caught and handled in the same way as exceptions raised by Python are caught.

```python
try:
  age = int(input('Enter age : '))
  if age < 0 or age > 120:
    raise ValueError

except ValueError:
  print('Invalid value for age')
else:
  print('Age is', age)
```

## Assertions

There is another statement that can also raise an exception which is the `assert` statement. It can raise only `AssertionError` exception and not any other type of exception. This statement is used as a debugging tool to detect programming bugs. Here is the syntax of this statement: `assert condition`

After the `assert` keyword, a condition is written. When the `assert` statement is executed, this condition is tested. If it is `True`, then the normal program flow continues. If it is False, then an `AssertionError` exception is raised. So, this statement is used to test the truthiness of a condition. You can think of this `assert` statement as a conditional `raise` statement.

```python
if not condition:
  raise AssertionError
```

This is somewhat equivalent to the `assert` statement. If the condition is not `True`, then an `AssertionError` exception is raised. We know that raising an exception means that an exception instance is created, and the normal program flow stops. Like other exceptions, if this exception is not handled, then it terminates the program. In the `assert` statement, after the condition, we can write an expression which is optional. `assert condition, expression`

If this expression is there, then it serves as the argument for initializer of the `AssertionError`. This is generally an error message. You can think of this statement as equivalent to the following code:

```python
if not condition:
  raise AssertionError(expression)
```

The expression that we have written after the condition is a string that represents the error message. This string was sent as argument when the exception instance was created. Instead of the string we can send any other expression also, but generally a string is sent that represents the error message. Now, let us see when to use these `assert` statements in our code and what is their use. They are used for debugging during development time; they can be used to put sanity checks in your code. They are useful debugging tools that alert you when there is some bug in your code.

## The End
