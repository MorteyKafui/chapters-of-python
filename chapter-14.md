# CHAPTER 14 - Inheritance and Polymorphism

By using inheritance, we can create a new class based on an existing class. In our new class, we get all the features of the existing class, and can also add new features and also override (replace) them as needed. Thus, we can easily create new classes by using the tried and tested functionality of existing classes. This reduces time and effort and simplifies the task of writing a new class.

Inheritance is an important feature of object-oriented programming; it is basically a mechanism of creating a new class from an existing class. The new class is the extended and modified version of the existing class. The main advantage of inheritance is that it facilitates code reuse and reduces code duplication. Inheritance also simplifies the design of the program as it lets you represent the real-world problems in a natural and better way. This makes the program more readable and easier to manage.

The existing class is called the **base class** and the new class is called the **derived class**. When you inherit from a class, everything from that class becomes automatically available in the derived class. The derived class inherits members from the base class and also contains its own members. Derived classes generally have some added functionality and provide more specific behaviour than the base class. Base class is also called the **parent class** or **super class** and the derived class is also called **child class** or **subclass**.

In object-oriented terms, the relationship between the base class and derived class is called **is-a relationship**. So, by using inheritance, you can implement an **is-a** type of relationship between classes.

## Inheriting a class

```python
class Person:
  def __init__(self, name, age, address, phone):
    self.name = name
    self.age = age
    self.address = address
    self.phone = phone

  def greet(self):
    print('Hello I am', self.name)

class Employee(Person):
  pass
```

When we write a new class from scratch, after the class name, we have the colon but when we write a class by inheriting from an existing class, after the class name we have the name of the existing class inside the parentheses. Since we are creating our `Employee` class by inheriting from the Person class, the name `Person` is inside the parentheses. The line `class Employee(Person):` means create a new `class Employee` that inherits from the `Person class`.

The Employee class has access to the `__init__ `method of the Person class, so all these arguments will be passed to that `__init__` method. This instance object will have all the attributes `name, age, address` and `phone`.

The `isinstance` function returned `True` for the `Person class` also, which proves the **is-a** relationship between `Employee` and `Person`. There is another built-in function named `issubclass` that can be used to check whether a class is subclass of another class.

```python
isinstance(emp, Employee)

issubclass(Employee, Person)
```

In the process of inheritance, the base class is not changed in any way. The derived class can differentiate itself from the base class in two ways: by adding new data members and methods or by overriding the methods of the base class.

## Adding new methods and data members to the derived class

While defining our derived class, we can add new data members and methods that are specific to our derived class.

```python
class Employee(Person):
  def __init__(self, name, age, address, phone,salary, office_address, office_phone):
    self.name = name
    self.age = age
    self.address = address
    self.phone = phone
    self.salary = salary
    self.office_address = office_address
    self.office_phone = office_phone

  def calculate_tax(self):
    if self.salary < 5000:
      return 0
    else:
      return self.salary * 0.05

```

We have defined two new methods in this class `__init__` and `calculate_tax`. The `__init__` method of the base class is inherited but our derived class needs some additional variables that need to be initialized so the inherited base method will not be sufficient. An `Employee object` needs to have 3 more instance variables which are salary, office_address and office_phone. In the `__init__` method, the first `4` parameters are the same as in `Person class` and after that we have added `3`
new parameters. The first four lines can be copied from the `__init__` of `Person class`, and then we have written three more lines to create the three attributes that are specific to the`Employee class`. Now when we create an `Employee instance`, we need to send seven arguments.

```python
emp = Employee('Raghu', 30, 'D4, XYZ Street, Delhi', '994477291', 8000, 'ABC Street, Delhi', '897657888')

```

## Overriding a base Method

To override a method, just define a method in the derived class with same name as in the base class.
So, if a derived class defines a method with same name as a method in base class, then the derived class method overrides the method of base class, it effectively hides the base class method. We have seen that this happened with the `__init__` method also. Since we have written a definition for `__init__` in the `Employee class`, the base
class version of `__init__` is hidden.

## Invoking the base class methods

While overriding a method, most of the times you want to extend the base class method instead of replacing it fully. So, mostly you need to begin by calling the base class method and then add special code that is specific to the derived class. The base class version can be accessed in the derived class by calling it explicitly using the base
class name. If the derived class is overriding a method and wants to use the functionality of the base version, then it is better to call the base method instead of just copying the code. This reduces code duplication and later if the base class method changes, the change will be reflected in the derived class method. A better way of calling the base class method is by using the `super` built in function.

```python
class Employee(Person):
  def __init__(self, name, age, address, phone, salary, office_address, office_phone):
    super().__init__(name, age, address, phone)
  self.salary = salary
  self.office_address = office_address
  self.office_phone = office_phone

```

Now there is no need of sending `self` as the first argument. Use of `super` is preferred because using base class name can create confusion in multiple inheritance, where a class inherits from more than one class. Writing `super` makes sure that all the base class versions are called, even from the classes that are inherited
indirectly as we will see shortly.

## Multilevel Inheritance

We can have multilevel inheritance which means that from the derived class we can further inherit another class. For example, from the `Employee class` we can inherit a class called `Teacher` and a class called `Accountant`.

## object class

`object class` is a built-in class from which every class automatically inherits. All built-in classes inherit from it and the custom classes that you define also inherit from it.

```python
class Person:
  pass

print(issubclass(Person, object)) # True
```

We defined a `Person class`, and we can see that it automatically inherits from the `object class`. So, when we don’t specify any base class, the class directly inherits from object class. The above class definition is equivalent to explicitly inheriting from the `object class`.

> In Python 3, this is redundant. It is not necessary to define a new class by deriving it explicitly from the `object class`. Any class that is defined without an explicit base class will be a derived class of object. So, every class inherits from the `object class` directly or indirectly. This class is at the top of any inheritance hierarchy in Python.

## Multiple Inheritance

Till now, the inheritance that we have seen is single inheritance, which means that a class inherits from a single class. Python supports multiple inheritance, meaning a class can inherit from multiple base classes.

```python
class X(A, B, C):
  pass
```

Here `class X` inherits from `classes A, B` and `C`. All the data members and methods of all the three base classes will be available in the derived `class X`. This is the syntax of defining a new class that inherits from multiple classes. All the base classes are placed inside the parentheses. This class definition creates a new class named `X` that inherits from `classes A, B` and `C`.

## Method Resolution Order(MRO)

The order in which Python searches for attributes in base classes is called **method resolution order (MRO)**. It gives a linearized path for an inheritance structure.

We can see the MRO for any class using the `__mro__` attribute or the mro method or by using the help function. If we have an instance and want to see its MRO dynamically, we can use the `__class__` attribute.

Thus we have seen that the method resolution order is used by Python when searching for attributes in base classes and it is also used by the built in function `super`. It is good to use `super()` whether you are using single inheritance or multiple inheritance. In multiple inheritance, the advantage is obvious. In single inheritance, also `super` can be beneficial if there are some updates made in the future like changing the name of the base class or switching to multiple inheritance. Thus, it makes the code more maintainable.

## Polymorphism

The meaning of the word polymorphism is the ability to take many forms. In programming, this means the ability of code to take different forms depending on the type with which it is used. The behaviour of the code can depend on the context in which it is used.

## Abstract Base classes

An abstract base class generally represents a model or an abstract concept – something that has no physical form; for example, Shape is an abstract concept, while Rectangle and triangle represent real things.

To mark a class as an abstract base class, we have to make use of the abc module of the standard library.

```python
from abc import ABC, abstractmethod

class Shape(ABC):
  @abstractmethod
  def area(self):
    pass

  @abstractmethod
  def perimeter(self):
    pass

  @abstractmethod
  def draw(self):
    pass

```

The `Shape` class now inherits from the `ABC` class of `abc `module. The methods `area, perimeter`, and `draw` are now decorated with the `abstractmethod` decorator, so they are abstract methods. By making a method abstract we force all the derived classes to implement that method. If the derived class does not implement an abstract method, then there will be an error while instantiating that class.

To make a class an abstract class we have to inherit from the `abc`.`ABC`class and it should have at least one abstract method in it. To make a method an abstract method we have to apply the `@abstractmethod` decorator from the `abc` module. We cannot create any instance object of an abstract class, and any class that inherits from an abstract class should override all its abstract methods.

In our example, `Shape` class is an abstract class so it cannot be instantiated. The derived classes that can be instantiated are called concrete classes. The abstract class provides a sort of blueprint or a template for its subclasses. It defines the methods that the subclasses should implement. An abstract class is not meant to be
instantiated; it exists only to be used as a base class that provides a basic foundation for the derived classes. Derived classes that implement the abstract methods are concrete classes that represent the real things that are modeled, and they can be instantiated.

An abstract class can have non-abstract methods as well, which the derived classes do not need to override. Most of the time, abstract methods have an empty body in the
abstract class. They are there only for defining the common interface, so their body generally contains a pass statement.

However, the abstract methods of an abstract class can contain some basic implementation that the concrete subclasses can call by using `super`. Even if the abstract method is implemented in the abstract base class, the subclass has to override it. The subclass can call the base implementation by using `super` and then add its own code for any additional tasks. You can also declare property methods, class methods, or static methods as abstract:

## The End
