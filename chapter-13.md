# CHAPTER 13 - Magic Methods

Magic methods are specially named methods that we can define to make our classes behave like built-in types. With the help of these methods, we can add, subtract or compare our instance objects or we can even index or slice them like other built-in sequences. These special methods begin and end with double underscore, to distinguish them from other user defined names. They are also called dunder methods due to the double underscore added before and after their name. Here are a few examples of dunder methods: `__init__, __add__, __mul__, __sub__, __eq__, __len__`

## String representation of an instance object

The magic methods `__str__` and `__repr__` are used for converting an instance object into a string.

The method `__str__` is invoked when an instance object is converted to a string by calling the `str` built-in function. It is also invoked when an instance object is printed using the print function because print implicitly calls the `str` built-in function.

The method `__repr__` is invoked by the `repr` built-in function, and it is also used to display the object in the interactive terminal. If `__str__` is not defined, then this method is invoked for str(obj) and print(obj) also.

Both `__str__` and `__repr__` methods return a string representation of the instance, but `__str__` is generally used for the end user of the class; it returns a human-readable and user-friendly string representation of the object. The string returned by `__repr__` is a descriptive and unambiguous string representation of the object. It returns a Python-interpretable text that can be used by programmers for debugging. This text is generally a valid Python expression from which you can re-create the instance object using the eval function.

## Construction and destruction of objects

When we instantiate a class, two magic methods are called. First `__new__` is called, it creates the object and returns it, and then `__init__` is called to initialize the newly created object. Most of the classes do not need to define `__new__`, the built-in implementation works in most of the cases. In rare cases, if you want to control the creation process of the instance object, you can define the `__new__`
method. The `__init__` method is defined in most of the classes for initialization purposes as we have already seen. The magic method invoked at the time of destruction of an object is `__del__`.

We know that the Python interpreter performs garbage collection to free up memory space, which means that it automatically destroys objects that are no longer in use. Each object has a reference count, which denotes the number of times the object has been referenced. When the reference count of an object reaches zero, the interpreter removes it automatically, and the memory occupied by the object is freed. This garbage collector works during the program execution and makes sure that there are no unused objects taking up space.

Another thing that we have seen earlier is that the `del` statement does not delete the object, it removes the reference and hence decreases the reference count of the object by one. For example, if names `x` and `y` are referring to the same object, then writing `del x` will not remove the object. It will only remove the name `x` from the scope and decrement the reference count of the object. When the name `y` will stop referring to the object (when it is reassigned, or removed using del statement or when it goes out of scope) the reference count of the object will drop to `0` and the interpreter will garbage collect it. Deleting names using the `del` statement is very rare, mostly the names go out of scope and when an object does not have any name referring to it, it is garbage collected.

The magic method `__del__` is automatically invoked when an object is destroyed by the garbage collector and this generally happens when the object’s reference count becomes zero.

## Making instance object callable

The method `__call__` is used to overload the calling syntax. If this method is defined in a class, then the instance objects of that class become callable objects, we can call them like a function. This method is automatically invoked when an instance object is called, which means that `obj(arg1, arg2, ……)` is equivalent to `obj.__call__(arg1, arg2, ……)`. The arguments that are sent to the object while calling are sent to this method.

## The End
