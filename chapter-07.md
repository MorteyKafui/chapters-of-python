# CHAPTER 7 - Comprehensions

Comprehensions are just syntactic sugar for the for loop syntax,
but they are considered more Pythonic. Code written using comprehensions is shorter, more readable, and often more efficient
than the equivalent code written using a `for` loop.

- List Comprehension

  List comprehension is an expression that creates a new list object.
  Syntax: `[expression for item in iterable]`

  This comprehension expression creates and returns a new list
  object.

  ```python
  squares = [num * 2 for num in range(2, 11)]
  print(squares)

  heights = [12, 45, 78, 77, 12, 14, 54]
  heights_cm = [ht * 2.54 for ht in heights]
  print(heights_cm) # [30.48, 114.3, 198.12, 195.58, 30.48, 35.56,137.16]
  ```

- Dictionary Comprehension

  A dictionary comprehension expression creates a new dictionary object. It generates key value pairs from one or more iterable.
  Syntax: `{key_expression : value_expression for item in iterable if condition}`

  ```python
  L = [2, 6, -4, 8, 3, 9, -5, -3]
  result = {n: n ** 2 for n in L}
  print(result) #{2: 4, 6: 36, -4: 16, 8: 64, 3: 9, 9: 81, -5: 25,-3: 9}

  {n: n ** 2 for n in L if n > 0}
  # {2: 4, 6: 36, 8: 64, 3: 9, 9: 81}

  ```

- Set comprehension

  A set comprehension creates a new set object.
  Syntax: `{expression for item in iterable if condition}`

  ```python
  text = 'Hello !!! My name is Anthony Gonsalves, and you are .... ??'
  result = {ch for ch in text if not ch.isalnum()}
  print(result) # {' ', '.', ',', '!', '?'}

  result = {ch for ch in text.lower() if ch.isalpha() and ch not in 'aeiou'}
  print(result) # {'t', 'd', 'g', 's', 'r', 'h', 'm', 'n', 'v', 'l','y'}

  ```

## `if` clause in list comprehension

To filter out unwanted values, we can append an if clause at the
end of the list comprehension.
Syntax: `[expression for item in iterable if condition]`

The condition after the `if` keyword will be evaluated for each item in the iterable. If the condition evaluates to `True`, only then the expression will be included in the output list.

```python
L = [3, 5, 7, 1, 8, 9, 4]
cubes = [n ** 3 for n in L if n % 2 == 0]
print(cubes) # [512, 64]

evens = [n for n in L if n % 2 == 0]
print(evens) # [32, 86, 66, 88]

words = ['apple', 'civic', 'board', 'noon', 'moon', 'lamp', 'madam']
palindromes = [word for word in words if word == word[::-1]]
print(palindromes) # ['civic', 'noon', 'madam']
```

## Ternary operator in list comprehension

Syntax: `[ expression for item in iterable if condition]`

In the place of expression, if we write an expression with a ternary operator, we can replace an item from the iterable with another value.

```python
L = [1, 2, -3, 6, 18, -9, 12, -5, 19, -8, 5]

values = [n if n > 0 else 0 for n in L]
print(values) # [1, 2, 0, 6, 18, 0, 12, 0, 19, 0, 5]

L = [1, 2, -3, 6, 18, -9, 12, -5, 19, -8, 5]
result = [n // 2 if n % 2 == 0 else n * 2 for n in L if n >= 0]
print(result) # [2, 1, 3, 9, 6, 38, 10]
```

> The if clause of the list comprehension cannot have an else clause. If we see an else in the list comprehension, it means a ternary expression has been used before the for keyword.

## The End
