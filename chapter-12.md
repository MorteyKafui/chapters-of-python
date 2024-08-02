# CHAPTER 12 - Object Oriented Programming

## Programming Paradigms

Programming paradigm is an approach to organize and structure your code; you can think of it as a way or style of programming.
The three common programming paradigms are _procedural programming paradigm_, _object-oriented programming paradigm (OOP)_ and _functional programming paradigm_.

In the procedural paradigm, there is a step-by-step procedure that is sequentially followed for solving a specific problem. It is implemented through code blocks called functions. The program is organised in a way such that the functions process the data of the program. In object-oriented programming, real world entities or concepts are modelled using objects. An object has both state and behaviour which means it contains both data and code to manipulate that data. In procedural programming, you model your program in terms of functions, while in object-oriented programming you model your program in terms of objects. Functional programming paradigm is a style of programming that uses built-in higher-order functions. A
higher-order function is function that takes another function as an argument or returns it as a result. Functional programming focuses more on ‘what to solve’ rather than ‘how to solve’.

## Introduction to object-oriented programming

- Classes and objects are the two main components of object-oriented programming. A class is a blueprint or template for creating objects. A class definition introduces a new type, and it describes the state and behaviour that the objects of this new type will have.Each object that is created from a class will have the data and behaviour specified in the class. To create the objects that represent users, we can define a class called User and to create objects that represent books, we can define a class called Book.

Classes encapsulate state and behaviour together - state refers to the internal data stored in the object and behaviour refers to the actions that can be performed by the object.

So, a class defines what data and methods should the object have, and the objects contain the actual data. Instantiation means creating an object using a class as the blueprint. The behaviour defined inside the class is shared by all the objects but data is not. Each object of a specific type behaves in the same way but has its own data. This means that the methods defined inside the class are shared by all the objects, so there is only one copy of each method which is used by all the objects. Each instance object maintains its own copy of data. So, you can think of class as a template that is used to create objects that behave in the same way but have their own data.

Polymorphism, which means one thing many forms, can also be implemented in object-oriented programming. Do not worry if some of the terms do not make sense now, things will become clearer once we start coding.

## Defining Classes and Creating Instance Objects

A new class is created by writing the `class` statement:

```python
class Person:
  pass

```

The keyword `class` is written, followed by the class name and a colon. Conventionally, the class names begin with a capital letter and are generally singular nouns. If there are multiple words in the class name, then they are joined using the CapWords convention, where the first letter of each word is capitalized.
When we execute this class definition, Python creates a class object and assigns it to the name `Person`.

```python
id(Person)
2769602751456

type(Person)
<class 'type'>
```

Like everything else, classes are also objects in Python; they are called class objects and their type is `type`. A class object is callable, we can instantiate a class object by calling it like a function, i.e., by putting a pair of parentheses around it. The call to class object returns an object which is called the instance of the class.
`p = Person()`

## Adding methods to the class

We have seen how to define a class and how to instantiate it, but the class that we have created is useless as it does not have any data or methods. Let us first add behaviour to our class with the help of methods. For that, we will write two def statements inside the class:

```python
class Person:
  def display(self):
    print('I am a person')

  def greet(self):
    print('Hello, how are you doing?')
```

These definitions of methods look like ordinary function definitions except that that there is parameter named `self`. We will talk about this parameter in a short while. You can think of methods as functions inside a class. To call a method, we will write the instance name, followed by a dot and the method name.

```python
p1 = Person()
p2 = Person()

p1.display()
p1.greet()
p2.display()
p2.greet()
```

This is how we can execute the methods using instance objects. You must be wondering how this code executed without any error because both the methods that we defined inside the class have one parameter each, but while calling the methods, we did not send any argument corresponding to the parameter named `self`. This worked because when a class method qualified with an instance is called, Python automatically sends the argument for the parameter `self`.

On executing this code, we get objects p1 and p2 printed in place of `self`. This means that the instance object that called the method, is printed in the place of self. In the first two calls, `self` refers to object `p1`, and in the last two calls, `self` refers to object `p2`. So, now we know that Python provides the instance that calls the method as the argument for the parameter `self`. Although you specify this
parameter `self` in the method definition, you do not have to provide a value for it while calling the method.

Generally, all methods inside a class should have this first parameter named `self`. There are some exceptions that we will see later on. Python uses this parameter to identify the instance object that calls the method. You can use any other name instead of `self`, but `self` is a convention widely adopted within the programming community. It is a very strong convention, so it is generally better to adhere to it.

## Adding instance variable

We have added behaviour to our Person class in the form of the two methods `display()` and `greet()`. These methods are shared by all the instance objects. Now, we will add data to our instance objects in the form of instance variables. Each instance object will maintain its own data which means that instance variables are not shared, each instance object will have its own copy of instance variables. An instance variable is created like you create any other variable in Python, by assigning a value to it. But since an instance variable is associated with an instance object, you have to use the dot syntax. Syntax: `self.variablename = value`

## Initializer

You can define a method named `__init__` in your class. This method will automatically be called right after the instance has been created. So, if you have any code you think should be executed just after the object creation, put that code inside this method.

```python
class Person:
  def __init__(self, name, age):
    self.name = name
    self.age = age
```

This name `__init__` is not a convention like naming of self, this is a special name and you cannot choose any other name for this method. The two leading and trailing underscores are also important. Because of these underscores, this method is generally called _dunder init_, where dunder is shortform of double underscore.

We do not have to call this method `__init__` explicitly, the interpreter will call it implicitly. Now you must be thinking, when we do no have to call this method, how will we send the arguments for the parameters name and age. These arguments will be sent when the object is instantiated.

```python
p1 = Person('Bob', 20)

p1.display()
p1.greet()

p2 = Person('Ted', 90)
p2.display()
p2.greet()
```

When you create instance objects, any arguments that you pass to
the class are passed to the `__init__` method. So, we have seen that the initialization work is automatically done by the interpreter if you define the `__init__` method. You can create and initialize all your instance variables in this method. Although instance variables can be created in any other method also, it is more readable and clearer if you create all instance variables in the `__init__` method. Also, there is no risk of the instance variables being accessed before they are defined. You can also perform any other startup task that you want, in this initializer method. For example, opening a file or setting up a network connection, or connecting to a database.
Like other methods, the first parameter to `__init__` is always `self`. After `self`, other parameters that are coded in `__init__` are generally used to give initial values to instance variables. These parameters can be given default values if required. The instance variables can also be initialized with values that are independent of parameters.

These methods, which have special names and double underscores before and after their names, are called **magic** methods in Python. The magic is that they are not called directly; they are called automatically in certain contexts.

To construct an instance, the magic method `__new__` is invoked. This method is responsible for creating the object by allocating memory for it. So technically, this is the actual constructor. As a beginner, you won’t need to use this method much; it is used while coding metaclasses, which is an advanced topic. The default `__new__` is automatically invoked if we do not provide our version, and in most cases, the default version serves the purpose.

The `__init__` (dunder init) is the initializer method. It is called immediately after the instance is created. It is the first method that is called on the newly created instance object. The `self` parameter passed to this method refers to the newly created object. So, the method `__init__` does not construct the instance object. It initializes an already constructed instance object.

You can have only one initializer method in a class, as there is no concept of function overloading in Python. However, it is possible to create instance objects with different types of data using class methods

## Class Variables

While modelling our objects, we might find that there is some data that does not vary for each instance, it is the same for every instance created from a particular class. Storing this piece of data in every instance object would be an unnecessary waste of memory, it would be good if we could have just one copy of that data and let each instance object access it. We can do this by defining variables at the class level; these variables are called **class variables** or **class attributes**.

```python
class Person:
  species = 'Homo sapien'

  def __init__(self, name, age):
    self.name = name
    self.age = age

  def display(self):
    print(f'{self.name} is {self.age} years old')

p1 = Person('John', 20)
p2 = Person('Jack', 34)

p1.display()
p2.display()
```

The variable named `species` is defined inside the class but outside any method, so it is a class variable. Class variables are generally placed at the top of the class definition, just below the class header. There is only a single copy of a class variable and it is shared by all the instances of the class. It belongs to the class, not to individual instance objects. The data of a class variable is stored in the class object itself, while the data of instance variables is stored in individual instance objects.

The value of species will be the same for all Person objects, there is no need to have a unique copy for each instance, so we have defined it as a class variable. Class variables are created in the class definition while the instance variables are created inside the methods, usually inside `__init__()`. A class variable can be accessed using the class name or the instance name.

```python
print(Person.species) # 'Homo sapiens'

print(p1.species) # 'Homo sapiens'

```

In fact, the class variables can be accessed even before any instance object is created. Inside the class methods, you can access a class variable by preceding it with class name or `self`.

So, if there is any value that needs to be shared by all instances of a class, then there is no need to waste memory by storing it in each instance object, we can make it a class variable and only one copy will be stored in the class object and all the instance objects can use the same copy. Class variables are created for storing data that does not vary for each instance while instance variables are created for data that can be different for each instance.

## Class and object namespaces

There is a namespace created for each class that is defined. When a class definition is executed, a new namespace is created for it. Anything defined at the top level of the class lives in this namespace, so all class variables and methods are part of this namespace. Basically, this namespace manages all names that are to be shared by all the instances of the class. When an instance object is created it gets its own namespace. Instance variables are part of this namespace. An instance gets access to all the names defined in the class namespace and the names defined in its own instance namespace. These namespaces are represented by the `__dict__` attribute of the class or the instance. After executing the previous program, we can see the `__dict__` attribute of the class and the instance objects.

## Class Methods

A class method is a method that is associated with the class itself not with any particular instance of the class. To make this method a class method we need to precede the method definition with the line `@classmethod`.

```python

@classmethod
def details(cls):
  print(f'Rate : {cls.rate}')
  print(f'Minimum Balance : {cls.min_balance}')
  print(f'Minimum Balance fees : {cls.min_balance_fees}')

```

The line `@classmethod` is a function decorator about which we will study later on, for now you can understand that adding this line turns a normal method into a class method.

The other change that we can see in this method is that the parameter is now named `cls`. This is because when a class method is called, the interpreter automatically sends the class object and not any instance object. The parameter is conventionally named `cls` because it is referring to the class object. You could write any other name here instead of `cls`, but just like `self`, this name `cls` is also a strong convention. This word is a short form of class; since class is a reserved word, this word cls is used.

Now, we can call this method with the class name. While calling, there is no need to provide any argument for the `cls` parameter, interpreter will automatically send the class as the argument for this parameter.

We do not need any instance to call this method. We know that all the class variables are created even before any instance object is created, so we can call this method even if we do not have any instance of this class.

So, the parameter `cls` refers to the class object inside the method definition, and that is why inside the method we have accessed the class variables through `cls` instead of hardcoding the class name.

A class method can also be invoked using an instance, but it makes more sense to invoke it using the class name. Class methods can work only with the class variables, they cannot access instance variables as they do not have a `self` parameter, and thus they have no access to the state of the instance. So, if we have to implement a method that needs to use only the class variables, we can make that method a class method.

The normal methods that we have been defining till now, have `self` as the first parameter and when they are called, they automatically receive the current instance as the first argument. These methods are more precisely called instance methods, to distinguish them from the class methods and static methods. So, when we simply say methods of a class, we generally mean instance methods, because the other two are not as frequently used.

## Static Methods

Sometimes we have to write methods that are related to the class but do not need any access to instance or class data for performing their work. These methods could be some helper or utility methods that are used inside the class but they can perform their task independently. There is no need to define these methods as instance methods or class methods as they do not need access to the instance object or the class object. We can define these methods as static methods by preceding them with the `@staticmethod` decorator.

Unlike instance methods and class methods, static methods do not have any special first parameter. They can have regular parameters, but the first parameter has no special significance. So, when a static method is called, Python does not send the class object or the instance object as the first argument. This is why these methods cannot access or modify the instance state or the class state.

```python

@staticmethod
def about():
  print('Information about BankAccount class……')
  print('…………')
  print('…………')
```

A static method can be invoked using either the class name or an instance name. So, when you have to create a helper or utility method, that contains some logic related to the class, turn it into a static method.

> If you have to make a method that needs to access instance variables, make it an instance method. An instance method has special first parameter named `self` that refers to the current instance object. If you have to make a method that needs to use only class variables and not instance variables, make it a class method. A class method has a special first parameter named `cls` that refers to the class object. When you need to create a general utility method, that needs to use neither instance variables nor class variables, make it a static method. Such a method depends only on its own argument values. It does not have any special first parameter.

A static method is just like a regular function, but it belongs to the class namespace. We know that the definition of a class defines a separate namespace and when you want to group functionalities under the class namespace, you can create static methods.

## Creating Managed Attributes using properties

Properties can be used to create data attributes with special functionality. If you want some extra functionality (like type checking, data validation or transformation) while getting or setting a data attribute, you can define a property which creates a managed attribute. The user can access and modify this managed attribute with regular syntax `(e.g. print(MyClass.x) or MyClass.x = 3)`, but behind the scene some method will be automatically executed while setting or getting the attribute. Property allows us to access data like a variable, but the accessing is handled internally by methods. This way, we can control attribute access by attaching custom behavior

_Setters_ (also know as mutators) and _Getters_ (also know as accessors) are generally used in object-oriented languages to restrict access to private variables and they allow you to control how these variables are accessed and updated. The getter and setter methods can also be used to make an attributeread only or write only.

This setter and getter methods approach is not preferred in Python, the Pythonic way of going about this whole thing would be to create a property. Properties allow us to write our class in a way that does not require the user of the class to call setter and getter methods.

The syntax of calling a property is same as the syntax for accessing a data attribute, although it is actually a method. The client code that uses a property does not look like a method call, instead it looks like a direct data attribute access.

```python
class Person:
  def __init__(self, name, age):
    self.name = name
    self.age = age

@property
def age(self):
  return self._age

@age.setter
def age(self, new_age):
  if 20 <= new_age <= 80:
    self._age = new_age
  else:
    raise ValueError('Age must be between 20 and 80')

def display(self):
  print(self.name, self._age)
```

We have added two special methods, and both are named `age`. Before the header line of these methods, we have added a line starting with `‘@’` symbol. The line `@property` makes the first method a **_getter_** method, and the line `@age.setter` makes the second method a **_setter_** method.

Now after this modification, the name `age` has become a property, we can access it like we access an instance variable. There is no need to call it like a method by using parentheses. The actual value of age is stored in the private variable named `_age`. The `age` attribute is a property which provides an interface to this private variable. The name of the property should be different from the attribute where we store our data.

Whenever we reference the attribute named `age`, the method with the line `@property` will be executed and whenever we assign something to it, the method with the line `@age.setter` will be executed. The method with `@property` is the getter method and the method with `@age.setter` is the setter method for the property.

The setter method accepts an argument which is used for setting the property. Note that the name of both methods is the same; they are different because they are prefixed with different `@` lines. These lines are decorators, they decorate these methods.

The getter method is always preceded with `@property` decorator and the setter method is preceded with the decorator that contains the property name followed by a dot and the word `setter`. If the name of your property is `salary` then the
decorator for its setter would be `@salary.setter`.

## Deleter method of property

We can also define a deleter method for the property, this deleter method defines what happens when a property is deleted. To create the deleter method, you have to define a method with the same name as the property and add the decorator with the word `deleter` in it.

```python
class Person:

  def __init__(self, name, age):
    self.name = name
    self.age = age

  @age.deleter
  def age(self):
    del self._age
    print('age deleted')

  def display(self):
    print(self.name, self._age)
```

A property allows access to an instance variable through methods, even though the method syntax is not used. By using the property syntax, we can define methods that are automatically called when an instance variable is referenced, assigned or deleted. We can define three methods for a property:

- Getter: executed when the attribute is accessed, preceded with decorator `@property`.

- Setter: executed when the value of attribute is set, preceded with decorator `@name.setter`.

- Deleter: Executed when the attribute is deleted, preceded with decorator `@name.deleter`

All three methods have same name which is the name of the property, they are distinguished because of the decorators. All of them take `self` as the first argument and the setter method takes an additional argument for setting the value of the property. If you want to provide a docstring for the property, specify it in the _getter_ method.

Properties can be used for attribute type checking and validation, for creating read-only or write-only attributes and for creating computed attributes. You can incorporate new behaviour in your instance variables, without any need to rewrite the existing client code. Thus, you can use a property to give new functionality to existing instance variables.

## Designing a class

If there is an attribute that should never be accessed by the
user, it should be made private by prefixing it with an underscore. There is no need of defining any property for it, as it should not be accessed from outside the class. These internal attributes are part of the implementation and should not be exposed in the public interface in any way. Then there are attributes that have to be accessed or modified by the user. You can start implementing your class by coding such instance variables as public and in future if you need more control over any instance variable, you can change it to a private attribute and write a property to access it. You should define a property only if it provides some extra functionality to the attribute. There is no point in defining a property that just gets and sets data without any extra logic. In other languages that do not have property mechanism, we need such setter and getters, but in Python we can always start with plain public attributes and promote them to properties whenever required without changing the interface. Public attributes that need no extra functionality while being accessed or modified should remain plain public attributes in the class. So, in Python, you can start with a very simple design and later introduce properties without changing the interface. There is no need to pollute your space with multiple setters and getters just to ensure that future changes are backward compatible.

## The End
