# CHAPTER 4 - Dictionaries and Sets

## Dictionaries

The dictionary data structure is a collection of key-value pairs. Each element of a dictionary is a key-value pair which is also known as an item.

## Creating a dictionary

- Using curly brackets `{}`

  ```python
  countries = {'IN': 'India', 'GR': 'Germany', 'MX': 'Mexico', 'JP': 'Japan'}
  print(countries)
  ```

- Using the `dict()` function
  We can create dictionaries from existing data that is present in other data structures like lists or tuples. The dict() function can be used to convert a sequence of two value sequences into a dictionary. The first item in the sequence is used as the key, and the second item is the value.

  ```python
  list1 = [['a', 1], ['b', 2], ['c', 3]]
  d1 = dict(list1)  # {'a': 1, 'b': 2, 'c': 3}
  ```

This dictionary contains four key-value pairs. The strings `'IN', 'GR', 'MX', and 'JP'` are keys, and the strings `'India', 'Germany', 'Mexico', and 'Japan'` are the corresponding values. The key-value pairs are separated by commas and are enclosed inside curly braces. In each pair, the key and the value are separated by a colon. The dictionary literal has been assigned to the name countries.

In our example dictionary, both keys and values are of str type. They can be of other types also, but there is a restriction on the type of keys. The keys can be of immutable type only; you cannot have a key of mutable type. Therefore, a key can be a string, an integer, a tuple, or any other immutable type; however, most of the time, it is a string. There is no such restriction on values; they can be of mutable or immutable types. So, a value in a dictionary could be a string, integer, list, tuple dictionary, or any other type.

The other restriction on keys is that they must be unique; duplicate keys are not allowed. Again, there is no such restriction on values. They can be duplicated, and the same value can be associated with any number of keys. So, you cannot have _key-value pairs_ where the keys are the same, but you can have _key-value pairs_ where the values are the same. A key can appear only once, while a value can occur many times. Like lists and tuples, you can have a trailing comma in a dictionary literal also.

Dictionaries are mutable data structures like lists, so a dictionary can shrink or grow at run time, and its elements can be changed. Like a list, a dictionary is also a referential data structure which means that it contains references to objects; both keys and values are object references.

Searching in dictionaries is performed by keys. You can provide the name of the key to retrieve the value associated with that key. For example, in our countries dictionary, we can get the name of a country from its abbreviation, which is used as the key. Dictionaries are highly optimized, so this lookup is very fast. If we try to structure our data of country names and abbreviations by using a list, it would be difficult to implement and also would be inefficient.

Now let us discuss how we can access a value corresponding to a given key. In lists and strings, we use an integer index inside the square brackets to access a value; in dictionaries, we will use a key inside the square brackets to retrieve a value. For example, the expression countries`['IN']` will give us the value associated with the key 'IN'.

```python
countries['GER'] # gets the corresponding value of GER in the dictionary. which is 'Germany'
```

> If the key we specify is not present in the dictionary, then we get a `KeyError`.

## Adding new key-value pairs

The following assignment statement will add a new key-value pair to the dictionary.

```python
d[k] = val
```

This will insert the key `k` with the value `val` in the dictionary `d`.

```python
countries["SA"] = "South Africa"
```

We know that duplicate keys are not allowed in a dictionary. Let us see what happens when we try to add a new key-value pair and the key already exists in the dictionary.
We do not get any error; assigning a value to an existing dictionary key replaces the old value with the new value.
If in a dictionary literal, a key is specified more than once, then also the interpreter will not complain, and it will assign the last occurrence of value to the key.

## Modifying Values

The syntax for adding a new key-value pair and modifying existing values is the same. If the key is not present, the assignment statement `d[k] = val` will insert the key and the value in the dictionary, and if the key is present, it will update the value.

```python
d[k] = val
```

## Getting a values from a key by using the get() method.

We have seen that we can access individual values in a dictionary using the key as the index. If we have a dictionary named d, we can write `d[k]` to access the value associated with the key `k`. The problem with this approach is that if the key `k` is not present in the dictionary `d`, then a `KeyError` will be raised.
To avoid this error, you can use the `get()` method. This method returns the associated value like `d[k]`, but if the key is not found, instead of raising an error, it returns `None`. You can specify another value to be returned instead of `None` if the key is not present. So, if you think there are any chances of the key not existing in the dictionary, it is better to use the get method instead of the square bracket notation.

```python
d.get(k) # returns value if found. If not returns None.
d.get(k,val) # returns values if found else returns the default value provided
```

The `get` method takes a key as the argument and returns the value associated with it. It takes an optional second argument, which is the value to be returned when the key does not exist.

```python
prices = {'pencil': 10, 'pen': 22, 'eraser':12,
'sharpener':13, 'marker':32}
prices['pen'] # 22
prices.get("pen") # 22
prices["stapler"] # KeyError
prices.get("Stapler") # None
prices.get("Stapler", 10) # 10
```

## Getting a value from a key by using the `setdefault()` method.

The `setdefault` method also accesses the value from a key, but if the key is missing, it will add that key to the dictionary. The `value` for that `key` is set to None or you can provide your own value also.

```python
d.setdefault(k) # returns value that is associated with the key k . if k is not pressent, returns None and adds the key k to dictionary with the value None.
d.setdefault(k,val) # returns the value associated with key k. if k is not present, returns val and adds the key k to dictionary with value val.
```

The `setdefault` method can take two arguments. The first
argument is the key for which you want to retrieve the value. The second argument is optional. It is the value that will be assigned to the key instead of the default `None`.

```python
prices = {'pencil': 10, 'pen': 22, 'eraser':
12, 'sharpener': 13, 'marker': 32}
prices.setdefault('pen') # 22
prices.setdefault('stapler') # None
prices.setdefault('gum',10) #10
```

## Getting all keys, all values and all key-value pairs.

The following three methods return special list-like iterable objects called dictionary views. These objects are dynamic, so any changes in the dictionary are reflected in these objects.

- `d.keys()`
  To get all the keys, use the `d.keys()` method.

- `d.values()`
  To get all the values, use the `d.values()` method.

- `d.items()`
  To get all the key-value pairs, use the `d.items()` method.

```python
prices = {'pencil': 10, 'pen': 22, 'eraser':
12, 'sharpener': 13, 'marker': 32}
prices.keys() # returns a dict_keys object
prices.values() # returns a dict_values object
prices.items() # returns a dict_items object
```

The methods `keys(), values(), and items()` return a
`dict_keys object, dict_values object, and dict_items object`. You can use the list function to convert these objects to list type if required.

These three methods do not return lists to save the time and memory used in creating a list that might have no use. For large dictionaries, lists also will be large and hence will consume more space. These methods return a view object, and if you want a list, you can convert explicitly. The dictionary view objects are iterable, and we can use them in a for loop to process all the items of a dictionary.

## Checking for the existence of a key or a value in a dictionary.

In the previous chapters, we saw that the `in and not in` operators can check whether a value exists in a list, tuple, or string. These operators can also check whether a key or a value exists in a dictionary. These membership operators can be used with the dictionary view objects to check for membership of keys and values.

```python
x in d
x in d.keys()
x in d.values()
(k,val) in d.items()
```

## Comparing dictionaries

The equality operators `== and !=` can be used to compare two
dictionaries. The expression `d1==d2` will return True if the two dictionaries contain the same key-value pairs. We can also use the use the `keys(), values(), and items()` methods with these operators. The other comparison operators `(<, >, <=, >=)` are not defined for a dictionary.

```python
d1 = {'x': 1, 'y': 2, 'z': 3}
d2 = {'x': 1, 'y': 2, 'z': 3}
d3 = {'x': 100, 'y': 200, 'z': 300}
d1 == d2 # True
d1 == d3 # False
d1.keys() == d3.keys() # True
```

## Deleting key-value pairs from a dictionary

The `del` statement can be used to delete a key-value pair from the dictionary. `del d[k]` will remove both the key k and its associated value from the dictionary. If the key is not present, then a `KeyError` will be raised. If you want to delete a key-value pair and store the deleted value in a variable, you can use the pop method. This method will delete the key-value pair, and it will return the value associated with the key. If the key is not present, then a KeyError will be raised. If you do not want the `KeyError` to be raised in case of missing key, you can send a second argument to the pop function, which will be returned if the key is not present. For example, the call `d.pop(k,-1)` will return `-1` if key `k` is not present.

```python
del d[k] # Removes key k and its associated value from the dictionary d
d.pop(k) # Removes key k and its associated value from the dictionary d, and returns the value d[k]
d.pop(k,val) # Returns val if key k is not present in the dictionary

```

> In lists, you could use the `pop()` method without any argument, and it would give you the last element, but in dictionaries, you cannot use `pop()` without an argument.

The method `popitem()` removes and returns a random key-value
tuple pair from the dictionary.

```python
prices = {'pen': 22, 'eraser': 12, 'gum': 13, 'ruler': 30}
prices.popitem() # ('ruler', 30)
prices.popitem() # ('gum', 13)
```

The method `clear()` removes all key-value pairs from the dictionary and makes it empty.

```python
prices.clear() # {} empty dictionary
```

## Combining dictionaries

We can copy the key-value pairs of a dictionary into another
dictionary by using the update method. The call `d.update(d1)` merges all entries of dictionary d1 into dictionary d. If there is a key that is present in both dictionaries, the value in dictionary `d` is overwritten by the value in dictionary `d1`.

```python
prices1 = {'apple': 10, 'mango': 15, 'banana': 20}
prices2 = {'grapes': 25, 'banana': 17, 'papaya': 12}
prices1.update(prices2)
print(p1) # {'apple': 10, 'mango': 15, 'banana': 17, 'grapes': 25, 'papaya': 12}
```

> All the entries of `prices2` are added to `prices1`. The key `'banana'` was present in both dictionaries, and we can see that the value in prices1 was overwritten by the value in `prices2`. The update method can also accept an iterable object of key-value pairs.

## Nesting of dictionaries

The values in a dictionary can be of any type; they can be of type dict also. When we have a dictionary as a value inside a dictionary, we get a nested dictionary.

## Aliasing and Shallow vs. Deep Copy

Dictionaries are also mutable structures like lists, so
you need to be careful about aliasing, and when you have a nested dictionary structure, you need to perform a deep copy instead of a shallow copy.

# Introduction to Sets

A `set` is an unordered mutable collection of immutable and unique objects. Sets are unordered, so sets do not maintain any order among their elements. So, they are not of sequence type. Sets are mutable, meaning an object of type set can be changed. We can replace existing elements of the set, add new elements, or remove elements from the set. A set is a collection of immutable objects, meaning it can contain objects of only immutable types like integers, strings, or tuples. It cannot contain mutable type elements like lists
or dictionaries. The elements need not be of the same types; a set can contain elements of different types. The most important point about sets is that it is a collection of unique objects, meaning duplicate elements are not allowed in a set. So, you can see that elements of a set are like keys of a dictionary. They have to be immutable and unique.

## Creating a `set`

- The call to `set()` function will create an empty set.

```python
s = set()
```

> We have only one way to create an empty set because empty curly braces {} are used to create an empty dictionary.
> `s = {} # an empty dictionary will be created`

```python
big_cities = {'London', 'Paris', 'Bangalore', 'Tokyo'}
primes = {2, 3, 5, 7, 11, 13, 17, 19}

```

Like lists, tuples, and dictionaries, sets are also referential structures, which means that they contain references to objects. The elements are not in any order; there is nothing like the first element or the second element. You can think of a set as just a bag of unique
values. In sequences like strings, lists, and tuples, the elements are ordered so they can be identified by their position; we could access an individual element by applying a numeric index. In dictionaries, elements are identified by keys, so there we can access an element by using a key as the index. But in sets, elements are neither ordered nor there are any keys, so we cannot use indexing to access an
individual element of a set. Sets do not support indexing or slicing as they do not have an inherent order. The most common operation performed on a set is testing the existence of an item.

```python
'Paris' in big_cities # True
city = 'Perth'
city not in big_cities # True
number = 11
number not in primes # False
```

Now the question is, how will you know that you need to create a set in your program? You can create a set when you have a collection of values whose order does not matter, and in your program, you will just need to know whether a value belongs to that collection or not. So, when you want to store some unique values whose order does not matter but search efficiency matters, you can use a set.

## Adding and Removing elements from a `set`

- s.add(x): Adds a new item `x` to the set `s`.
- s.pop(): Removes an arbitrary element from `s`.
- s.remove(x): Removes `x` from set `s`, raises `KeyError` if `x` not present.
- s.discard(x): Removes `x` from set `s`, no effect if `x` not present.
- s.clear(): Removes all elements from `s`.

```python
cities = {'Cairo', 'Mumbai', 'Agra', 'Bengaluru', 'Rome', 'Perth', 'Bareilly', 'Bern'}
cities.add('Delhi') # {'Bern', 'Agra', 'Mumbai', 'Cairo', 'Perth','Bengaluru', 'Bareilly', 'Rome', 'Delhi'}

cities.remove('Bern') #{'Agra', 'Mumbai', 'Cairo', 'Perth', 'Bengaluru', 'Bareilly', 'Rome', 'Delhi'}

cities.remove('Tokyo') # KeyError: 'Tokyo'

cities.discard('Tokyo')
print(cities) #{'Agra', 'Mumbai', 'Cairo', 'Perth', 'Bengaluru', 'Bareilly', 'Rome', 'Delhi'}

city = cities.pop()
print(city) # Agra
print(cities) # {'Mumbai', 'Cairo', 'Perth', 'Bengaluru', 'Bareilly', 'Rome', 'Delhi'}

```

The copy method of set type returns a shallow copy of the set. The built in functions like `len(), sum(), max(), min(), sorted(), all(), any()` work on sets also.

# Frozenset

A frozenset is the immutable version of a set. Once a frozenset is created, it cannot be changed. Since they are immutable, they can be used as members in other sets and as dictionary keys. You can think of a `frozenset` as a read-only set. frozensets support the same operations as sets, except the operations that change the contents. So, methods like add, remove, pop, and update are not applicable for frozensets. You can create a frozenset by sending an iterable to the frozenset function.

```python
weekdays = frozenset({'Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday'})
weekend = frozenset(['Saturday', 'Sunday'])

vowels = frozenset('aeiou')
type(weekdays) # <class 'frozenset'>
weekdays # frozenset({'Thursday', 'Monday', 'Tuesday' 'Wednesday', 'Friday'})
print(weekend) # frozenset({'Saturday', 'Sunday'})

print(vowels) # frozenset({'a', 'i', 'o', 'e', 'u'})
```

> When you need an immutable version of a set, you can use a
> `frozenset`.

## The End
