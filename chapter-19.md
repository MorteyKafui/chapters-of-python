# CHAPTER 19 - Context Managers

They are generally used to automate common resource management patterns like opening and closing files, connecting and disconnecting from a database, and locking and unlocking threads. Resources like files, database connections, or network connections are limited, and not managing them properly can lead to resource leaks, slow down, or sometimes data corruption. Whenever we work with such limited resources, we have to ensure that they are properly released after use.

The context managers and the `with` statement help in the safe acquisition and guaranteed release of system resources. They also help avoid repetition of acquisition and release code. The most common use of context managers is to manage resources like files, locks, databases, or network connections; however, you can use them anywhere where you need to surround some portions of your code with some pre and post-code.

## `with` statement

```python
with expression as var:
  statements
```

The `expression` should be a context manager object, or it should produce a context manager object. When this `with` statement is executed, the first thing that happens is that the `expression` is evaluated and it gives an object which is a context manager. Now let us see what is a context manager.

A context manager is an object that follows the Context Management Protocol. This protocol states that an object should support `__enter__` and `__exit__` methods to be qualified as a context manager.

The object that is returned by the expression should support the two magic methods `__enter__` and `__exit__`, then only it can be used in the with statement.

Any class that implements a context manager should have these two magic methods defined. When we instantiate such a class, the objects that we get are context managers.

```python
class CM():
  ……………
  def __enter__(self):
    pass

  def __exit__(self, exc_type, exc_value, traceback):
    pass

  ……………
```

The `__enter__` method takes only a single argument, which is self, and the `__exit__` method takes three more arguments in addition to self. So, instances of any class that defines `__enter__` and `__exit__` methods conform to the Context Management Protocol and thus can be used in the with statement.

Now, let us see the flow of control when the with statement executes. As we have seen, first of all the expression written after the `with` keyword is evaluated and we get a context manager object. After this the `__enter__` method of this context manager is called. The value returned by the `__enter__` method is assigned to the variable that is specified after the as keyword.

The value that is returned by `__enter__` is something that we
would like to use inside the with code block, this is generally the context manager itself, but it can be anything else also. So, mostly the `__enter__` method returns self but it can return something else, too. The as keyword and the variable written after it are optional. If they are not present, the value returned by `__enter__` is just discarded. This is why it is not necessary for `__enter__` to return any value.

After the `__enter__` method has finished executing and its return value has been assigned to var, the body of the with statement executes, so all the statements inside the with code block are executed.
After all the statements have been executed, the `__exit__` method of the context manager is called and executed. So, this is how the with statement works.Here is a review of the control flow:

1. Expression is evaluated to get a context manager object.
2. The `__enter__` method of the context manager is executed.
3. Value returned by the `__enter__` method is assigned to `var`
4. Statements inside the `with` block are executed.
5. The `__exit__` method of the context manager is executed.

If an exception occurs during the execution of statements inside the with code block, then the rest of the statements in the with code block are skipped, and the control is transferred to` __exit__`. So, the` __exit__` method is always called when the with code block is exited, no matter how the block is exited whether it is due to the end of the block, a return statement or an exception. Like the finally block of the try statement, the context managers’s` __exit__` method is guaranteed to be always called, and so you can place any cleanup code in this method.

## The End
