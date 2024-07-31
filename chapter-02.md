# CHAPTER 2 - Strings

A **string** is a sequence of characters.
In Python, the type `str` is used to represent a string. You can specify a string literal by enclosing a sequence of characters in either single quotes or double quotes. A string literal can contain zero or more characters, including letters digits, special characters, and space. The enclosing quotation marks are not stored as part of the string; they are used to delimit the string.
Examples of string literals are:

- Empty("") or Empty('') string:

```python
username = ""
username = ''
```

- Single quote(''):

```python
message = 'Hello Python!'
```

- Double quotes(""):

```python
message = "Hello Python!"
```

> You can also enclose or delimit strings in triple single quotes or triple double quotes like this:
> message = '''Hello World'''
> message = """Hello World"""

If the single quote has to be used as an actual character inside the string, the string can be enclosed in double-quotes. If a double quote must be used as an actual character inside the string, the string can be enclosed in single quotes.
You can use single or double quotes to enclose the string literals in your program. Whichever style you choose, it is better to stick to it. It is not a good idea to mix the two styles.

## Indexing

To access a single character inside the string, we must specify a numeric index inside square brackets. Indexing is 0 based, so the first index is 0.

```python
word = "Photosynthesis"
first_char = word[0] # To access the first character in a string
print(first_char) # P
```

If a string has `n` characters, the valid index values are from `0` to `n-1`.
Trying to access an index larger than the string will result in an error, `IndexError`

```python
message = "hello"
print(message[10]) # Results in IndexError
```

## Getting the length of a string

The built-in function `len()` gives the length of the string, which is equal to the total number of characters in the string.

```python
message = "Hello"
message_length = len(message)
print(message_length) # 5
```

The expression `len(sstring)-1` can be used as an index to access the last character of the string.

```python
message = "Hello"
last_char = message[len(message) - 1] # Last character in string
last_char = message[len(message) - 2] # Second last character in string
print(message_length) # o
```

We can also access the last character in a string by simply writing `string_var[-1]`.

## Strings are Immutable

Strings are immutable, meaning you cannot change a string object in any way. When you try to modify a string you'll get a `TypeError`.

```python
message = "Hello"
message[2] = "P" # TypeError
```

Tyring to modify a string will result in an error because strings are immutable. But we can reassign a variable to another object.

By reassigning a string variable, you can change a string variable without violating the immutability of the string object. It might seem inefficient that a new string object is created every time a string must be changed. However, practically, it is not so, as Python's garbage collector will automatically reclaim the space occupied by any unused objects.

## String Slicing

With square brackets, we can also access a portion or slice of a string which is called **slicing**
To extract a part of the string, we must specify 2 integers inside square brackets. `string[i:j]`

Inside the square brackets, we have two integers, i and j, separated by a colon. The expression s[i:j] is a slice of the string; it gives us a new string object that is a copy of the portion of the string s from index i to index j-1. Note that the first index is included while the second index is excluded. So, the slice s[i:j] returns a new string object that contains all the characters of string s, from index i up to (but not including) index j. The original string object does not change.

```python
word = "technology"
word[2:6] # chno
```

The expression `word[2:6]` gives us a new string object that contains all the characters of string s from index 2 to index 6. The sliced object can be assigned to a name.

While writing the slicing expression, we can omit the first or the second number or both. If we omit the first index, it is assumed to be 0, i.e., the beginning of the list. So, the slice s[:j] indicates a part of the string s from index 0 to index j-1. It is equivalent to writing s[0:j]. If we omit the second index, it is assumed to be the end of the string. So, the slice s[i:] indicates a part of the string s from index i to index n-1 where n is the length of the string. It is equivalent to writing s[i:n].

```python
message = "Hello"
message[2:] # slice from index 2 to the end of string, thus n-1
message[:3] # slice from the index 0 to index 3-1
```

We can omit both the indices inside the brackets. Therefore, the slice s[:] extracts the entire string from the beginning till the end. It gives an exact copy of the entire string. It is the same as writing
s[0:n].

```python
message = "Hi"
message[:] # gives exact copy of string
```

You can specify a negative index also while slicing.

```python
message = "hello"
message[0, -1]
```

Now, let us write a slice with a negative number as the first index.

```python
message = "hello"
message[-3] # the last 3 chars
```

When both the indexes are equal, we get an empty string.

```python
message = "hello"
message[2:2] # empty string ""
```

While slicing, you can also use a third integer inside the square brackets, which is the stride or step of the slice. `string[i:j:k]` from index `i` to index `j-1` with a step of `k`

```python
message = "hello from python"
message[3:6:2]
```

The slice `s[i:j:k]` will extract characters from index `i` to index `j-1`, with each subsequent index incremented by `k`. When the step is omitted, it is assumed to be `1`, so `s[i:j:1]` is equivalent to `s[i:j]`. In the previous examples that we had written, it was assumed to be `1`. We can give negative steps also. In the slice `s[6:1:-1]` we start at `6` and add `-1` each time, so we get indexes `6,5,4,3,2`. Thus, the effect of using a negative slice is that we get the items in reverse order. The slice `s[::-1]` will give the whole string in reverse order.

```python
message = "Hello from python"
message[::-1] # reverses the string
```

## String Concatenation and Repetition

We know that when the operators `+` and `*` are used on numeric types, they add and multiply numbers. These operators can also be used on strings, but they are interpreted differently. The operator `+` performs string concatenation, and the operator `*` performs string repetition.
String literals or string variables can be combined by using the `+` operator.

```python
"Hello" + "world" # "Helloworld"
"Hello" + " " + "world" # "Hello world"
name = "Bob"
message = "Hello" + " " + name # "Hello Bob"
```

The asterisk symbol, when used with a string and integer, acts as a repetition operator. We can use the repetition operator to repeat a string.

```python
name = "Tim"
name * 5 # "TimTimTimTimTim"
```

The expression name `* 5` returns a string object that contains the characters of the string name repeated _five_ times. The integer denotes the number of times the string is repeated.

## Checking Membership

The `in` and `not in` operators can be used to test for the existence of a character or substring inside a string. The `in` operator returns `True` if a character or substring exists in the given string; otherwise, it returns `False`. The `not in` operator returns `True` if a character or substring is not present in the string.

```python
message = "Good morning"
"Good" in message # True
"god" in message # False
"god" not in message # True
"morning" not in message # False
```

## Creating Multiline Strings

A string literal enclosed in single or double quotes cannot span more than one line of a program. Such a string should be contained in a single line only. The ending quote should appear on the same line as the starting quote. You will get a syntax error if you try to write a multiline string inside single or double quotes.

A better and more common way is to use triple-quoted strings. If you put a string literal inside triple quotes, it spans across multiple lines naturally. The triple quotes can consist of three consecutive single quotes('''abc''') or three consecutive double
quotes("""abc""").

```python
s = '''Let us get up and get going, With a strong heart for whatever may come our way. Keep working, keep trying, Learn to work hard and be patient each day.'''

s = """ Let us get up and get going, With a strong heart for whatever may come our way.Keep working, keep trying, Learn to work hard and be patient each day."""
print(s)
```

The newline characters are naturally embedded in a string delimited by triple quotes. Any spaces at the beginning of the line will also be included in the string. If we display the string on the prompt instead of printing it using the `print()` function, we will see the newlinecharacters.

When you delimit a string literal inside triple quotes, Python adds a newline character at the end of each line. When you print such a string with the print function, you can see the original lines because each newline character is interpreted. When we used ackslash to join the lines, then the newline was not added automatically. If you want to prevent some newlines in a triple-quoted string, add a backslash at the end of those particular lines.

## String Methods

The `str` type supports many methods that can be dot suffixed to the name of the string. We have seen that str is an immutable type, so it does not provide any methods that change the original string object. All methods that seem to make changes in the string are designed such that they return a new modified string object. They do not touch the original string object because they are not able to, as objects of type str are immutable.

- **Case Changing Methods**

  - upper(): Converts all characters to uppercase.

  ```python
  message = "hello"
  message.upper() # HELLO
  ```

  - lower(): Converts all characters to lowercase.

  ```python
  message = "HELlO"
  message.lower() # hello
  ```

  - capitalize(): Capitalizes the first character.

  ```python
  message = "hello world"
  message.capitalize() # Hello world
  ```

  - title(): Capitalizes the first character of each word.

  ```python
  message = "hello world"
  message.capitalize() # Hello World
  ```

  - swapcase(): Swaps case of all characters.

  ```python
  message = "heLLo WorlD"
  message.swapcase() # HEllO wORLd
  ```

> To get an up-to-date list of methods, you can call `dir(str)` or `help(str)` on the interactive prompt. To get the description of a particular method, type `help(str.methodname)` on the prompt.

- **Character Classification Methods**

  - isalnum(): Returns True if all characters in s are alphanumeric.
  - isalpha(): Returns True if all characters in s are alphabetic.
  - isdecimal(): Returns True if there are only decimal characters in s
  - isdigit(): Returns True if all characters in s are digits
  - isidentifier(): Returns True if s is a valid identifier.
  - islower(): Returns True if all letters in s are lowercase.
  - isupper(): Returns True if all letters in s are uppercase.
  - istitle(): Returns True if s is a title cased string.
  - isnumeric(): Returns True if all characters in s are numeric.
  - isprintable(): Returns True if all characters in s are printable.
  - isspace(): Returns True if all characters in s are whitespace

- **Aligning Text Within Strings**

  - ljust(size): Returns the string left justified in a string of length size.
  - rjust(size): Returns the string right justified in a string of length
    size.
  - center(size): Returns the string centered in a string of length size.

  > The methods ljust(), rjust(), and center() left justify, right justify, or center a string, respectively, such that the string fits within the number of spaces provided by the argument size. Here, size is the total length of the string after padding. These methods can be used in printing tabular data. If size is less than the length of the string, there is no change.

- **Removing unwanted Leading and Trailing Characters**

  - lstrip(chars): Returns a copy of the string with leading characters removed.
  - rstrip(chars): Returns a copy of the string with trailing characters removed.
  - strip(chars): Returns a copy of the string with both leading and trailing characters removed.
    > `lstrip()` and `rstrip()` remove characters from the left and right sides of the string, respectively, while `strip()` removes characters from both the left and the right sides. The set of characters to be removed is specified as a string argument. All the characters present in the string argument will be removed from the left, right, or both sides of the string.

- **Searching and Replacing Substrings**
  - find(substr): Returns index of the first occurrence of the given substring. If not found, returns `-1`.
  - index(substr): Returns index of the first occurrence of the given substring. If not found, raises `ValueError`.
  - rfind(substr): Returns index of the last occurrence of the given substring. If not found, returns `-1`.
  - rindex(substr): Returns index of the last occurrence of the given substring. If not found, raises `ValueError`.
    > The methods find and index return the index of the first occurrence of the given substring. If not found, find returns `-1` while index raises a `ValueError`. The methods `rfind` and `rindex` are the same as find and index except that they search through the string backward, i.e., from right to left, so they find the last occurrence of the substring.
  - count(substr): Returns the number of occurrences of the specified substring in s.
  - startswith(substr): Returns True if s starts with the specified substring, False otherwise.
  - endswith(substr): Returns True if s ends with the specified substring, False otherwise.
  - replace(string1,string2): Returns a copy of the string with all occurrences of the first string replaced with the second string.
    > In all these methods, you can restrict the search by specifying, optional arguments start and end, as in a slice. To substitute a substring with another we can use the method replace. It returns a copy of the string with all occurrences of the first string replaced with the second string. As usual, the original string remains unchanged, and a new string object is returned. You can restrict the number of replacements by providing a third argument. That argument represents the number of occurrences that have to be replaced.

## String Comparison

The operators `is` and `is not` are used to compare the identity of strings (and other objects). They check whether the two strings occupy the same space in memory.
The comparison operators `==, !=,<, >, <= and >=` are used to compare strings. As usual, they return a Boolean value `True` or `False`. Two strings are considered equal if their content is exactly the same.

```python
s1 = "Python"
s2 = "Python"
s1 == s2 # True
s1 != s2 # False
```

> The comparisons performed by the comparison operators are casesensitive. For example, 'Python' and 'python' will not be considered equal. To ignore case and perform case-insensitive comparisons, you can convert both strings to either lowercase or uppercase by using the upper and lower methods.

The `casefold()` method can also be used for caseless matching of the strings, as it returns a casefolded copy of the string. This method will work properly even if your string contains Unicode characters.

```python
s1 = "Python"
s2 = "python"
s1.casefold() == s2.casefold() # True
```

## String Formating

String formatting also allows us to interpolate values of variables into strings, which means that we can insert values inside strings using different formats. You need to format strings for better display on the screen. String formatting is also required when you need to substitute variables.

- format() method: Formats a string using placeholders.

```python
username = "Tim"
message = "Hello"
full_message = "{} {}, it's nice meeting you.".format(message, username)


name = "Alice"
age = 30
s = "Name: {}, Age: {}".format(name, age)
print(s)
```

> The curly braces act as placeholders for the data, and the values are sent as arguments to the format method.

- f-strings: Formatted string literals (Python 3.6+).

```python
username = "Tim"
message = "Hello"
full_message = f"{message} {username}, it's nice meeting you."


name = "Alice"
age = 30
s = f"Name: {name}, Age: {age}"
print(s)
```

Using these `f-string` literals, you can embed Python expressions inside a string literal using curly braces. They are called _f-strings_ because you get a formatted string literal by prefixing a string with the letter `f`. So, when we have a string literal prefixed with `f`, any variable inside curly braces is substituted with its value. You can see that this style is much clearer than the previous two. It is the simplest one because you can directly insert the names inside the string literal.
