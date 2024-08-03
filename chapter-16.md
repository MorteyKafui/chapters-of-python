# CHAPTER 16 - Decorators

A decorator is a callable that takes a callable as input and returns a callable. This is the general definition of a decorator. The callable in this definition can be a function or a class.

Decorators are used to add some functionality to a function. They allow you to execute some extra code before or after the execution of a function. This extra work is done without making any changes to the source code of the function. So, by using a decorator we can extend the behavior of a function without actually modifying its code.

A decorator is a function that takes another function as an argument, decorates it with the extra functionality and gives you a decorated function as the result. Decorators are functions, so they are reusable pieces of code; we can apply a decorator to different functions to add the same functionality to all of them without changing their code.

There are some decorators that are built-in `(e.g., classmethod, staticmethod)` and many third-party libraries also provide decorators for some common functionalities. These all are readymade decorators that we can use to decorate our functions. We can also define our own decorators; these are called user
defined decorators.

## Writing your first decorator

```python
def my_decorator(fn):
  def wrapper():
    print('Hi … Starting execution')
    fn()

    print('Bye … finished executing\n')
  return wrapper

decorated_func1 = my_decorator(func1)

```

The decorator function takes a function as argument and decorates it, so now let us see how it does the decoration. We have defined an inner function and named it `wrapper` because it will wrap our original function with the extra code. Inside this `wrapper` function we have called the parameter function `fn`. This function call will actually call the undecorated original function that is sent as an argument. As we have seen before, the inner function gets access to the variables of the outer function, so the `wrapper` function can access `fn`, which is the parameter of the outer function.

## Automatic decorator syntax

The reassignment statement that we are writing to decorate a function is the manual way of applying decorator to a function. This pattern is very common so Python provides an automatic way of applying the decorator. You just need to add the `@` sign and decorator name before the definition of function that you want to decorate.

```python
@my_decorator
def func3():
  print('Learning decorators')
```
