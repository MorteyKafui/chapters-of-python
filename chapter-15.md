# CHAPTER - Iterators and Generators

## Iterables

An iterable object is capable of returning its members one at a time. Such an object can be iterated over in a for loop and in other iteration contexts. Most built-in containers are iterables, e.g., lists, tuples, sets, dictionaries, strings.

An object is considered iterable if we can get an iterator from it when it is passed to the `iter` built-in function. So, an iterable object responds to the built-in function `iter` by returning an iterator object.

## Iterators

An iterator is an object that represents a stream of data. It produces a stream of values, one at a time. An iterator responds to the built-in function `next` by returning the next item from the data stream that it represents. When you pass an iterator object to the function next, it returns the next item. When there are no more items left, it raises the `StopIteration` exception.

An iterable is an object that, when passed through the `iter` function, returns an iterator, and an iterator is an object that produces the next item using the `next` function, and when there are no more items, it raises a `StopIteration` exception. When an iterator is passed to the `iter` function, the iterator itself is returned. This way, you can say that an iterator is always an iterable object because it responds to the `iter` function by returning an iterator. But an iterable object is not always an iterator, as it cannot respond to the function `next`. We can think of iterators as special iterables that act as their own iterators.

## Generators

There are two types of generators: generator functions and generator expressions. Both of them are used to create generator objects which are actually iterators. A generator object is a kind of iterator, and we get a generator object by writing a generator function or a generator expression.

A generator function is like a generator factory, you can call it many times to get generator objects, each one will have their own state information, independent of each other.

## Generator expressions

Generator expression is an expression that returns an iterator also known as generator object. This generator object returns values one by one when used in an iteration context such as for loop.

## The End
