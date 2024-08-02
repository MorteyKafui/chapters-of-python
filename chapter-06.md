# CHAPTER 6 - Loops

A loop or an iterative control statement is a control statement that is used for repeated execution of a block of statements. We need loops when we want to do something more than once. Instead of writing the same statements repeatedly in our code, we can use loops to automate the
repetition. In Python, we have two loops: `while` loop and `for` loop.

## `while` loop

In `while` loop, there is repeated execution of a block of statements while a given condition is `True`.

```python
while test_condition:
  statementA
  statementB
  statementC

```

The `while` keyword is followed by a test expression, also called the loop condition, which is followed by a colon. This colon marks the start of the statement block, which is to be executed repeatedly while the test expression is true. The statement block is also called the loop body, and
the indentation separates this loop body from the header line.

First, the test expression is evaluated; if it is `True`, the statement block executes, and then the control
returns to the test expression. If it is `True`, again the block executes and then the test expression is checked. This process continues till the test expression is `True`. When it becomes `False`, the loop terminates, the control comes out, and the next statement out of the loop is executed. So, this loop keeps running while the test expression at the top is `True`. One complete execution of a loop is called an iteration.

```python
count = 1

while count <= 10:
  print("Hello from Python" )
  count += 1 # same as count = count + 1

print("Done!")
```

> To avoid an infinite loop, remember to place an update statement inside the loop body and make sure that the condition becomes False eventually at some point.

## `for` loop

Like the `while` loop, the `for` loop is also used to repeatedly execute a block of code, but unlike a `while` loop, it is not based on a condition. It is a collection-controlled loop, and it iterates once for each element in the collection.

```python
for item in iterable:
  statementA
  statementB
  statementC
```

We have the keyword `for`, then a variable name, another keyword `in`, and then an _iterable_ name. This iterable can be any iterable structure like a _string_, _list_, _tuple_, _set_, _dictionary_, or even a _file_. The elements in this iterable are assigned to the variable named _item_ one by one, and the statement block is executed once for each item.

```python
data = [3, 5, 9, 8]

for number in data:
  print(number) # 3 5 9 8
```

When the loop starts, the first element in the list
is assigned to the iterating variable named number, and the statement block is executed. On the next iteration, the second element of the list is assigned to the variable number, and the statement block is executed. This process continues until the entire list is exhausted. So, the loop
terminates when this loop body has been executed for each element of the list.

## Unpacking in `for` loop header

- unpacking list tuple

```python
L = [('John', 20), ('Sam', 15), ('Dev', 21), ('Ryan', 10)]

for name, age in L:
  print(name, age)
```

- unpacking nested list

```python
L = [['John', 20], ['Sam', 15], ['Dev', 21], ['Ryan', 10]]

for name, age in L:
  print(name, age)

for name, _,  in L: # ignore an item
print(name)
```

- unpacking a dictionary

```python
D = {}

for key in D:
  print(key)

for key in D.keys():
  print(key)

for value in D.values():
  print(value)

for item in D.items():
  print(item)
```

The `items()` method returns the `keys` and `values` packed inside tuples. In each iteration of this for loop, the tuple returned by this method will be assigned to the variable item. We can unpack the tuple in the header to get the key and value.

```python
D = {}

for key, value in D.items():
  print(f'key is {key}, value is {value}')
```

## Premature termination of loops using the `break` statement

Normally, a `while` loop terminates when the loop condition becomes `False`, and a `for` loop terminates when the whole iterable has been iterated over. However, in some situations, we might need to come out of the loop even before the loop condition becomes `False` in a `while` loop or before the iterable is exhausted in a `for` loop. In these cases, we can use the `break` statement to terminate the loop immediately. The `break` statement is written inside a loop to prematurely terminate it when some particular condition is met. Practically, this break statement appears inside an `if` statement, so it executes conditionally.

So, the `break` statement is used to break out of a loop, even if the loop condition has not become `False` or the iterable has not been completely iterated over.

```python
trip = ['Milan', 'Venice', 'Munich', 'Vienna', 'Budapest', 'Prague', 'Berlin', 'Amsterdam', 'Paris' 'Nice']

for city in trip:
  print(city, end=' ')
  if city == 'Berlin':
    break
```

## `continue` statement

The `break` statement terminates the loop, but there may be situations when we need to terminate only the current iteration, not the whole loop. In these cases, we can use the `continue` statement to jump directly to the next iteration without finishing the current iteration.

Like the `break` statement, the `continue` statement is allowed only inside a loop body and with an if condition. When a `continue` statement is encountered in a loop body, it does not execute the remaining statements of the current iteration and immediately takes control to the top of the loop. In a `while` loop, the control goes to the test expression, and in the `for` loop, the next item from the collection is processed. So, the `continue` statement terminates the current iteration and continues with the next iteration of the loop.

```python

for i in range(100):
  if i % 10 == 0:
    continue

print(i)

```

## `else` block in loops

A loop can terminate in two ways, either naturally or prematurely. A `while` loop terminates naturally when the test condition becomes `False` and prematurely when break is encountered. A `for` loop terminates naturally when the loop has iterated over all items of the iterable and
prematurely when the `break` is encountered.

Both `while` and `for` loops can have an `else` clause.

```python
while test_condition:
  statement1
  statement2

  for item in iterable:
    statement3
    statement4
  else:
    StatementA
    StatementB
else:
  statementC
  statementD
```

The statements in the `else` block will be executed only once when the loop terminates naturally without encountering a `break` in the first block. If the loop ends due to a `break` statement, the `else` block is skipped; statements inside it will not be executed.

If the `else` statement is used in a for loop, the else block is executed when the loop has exhausted iterating over the iterable. If the `else` clause is used in a `while` loop, the `else` block is executed when the loop condition becomes `False`. So, if you come out of the loop normally without breaking anywhere in between, the `else` block will be executed.

We can see that if the loop terminates due to `break`, the `else` block is not executed. But if the loop terminates naturally, the block is executed.

The `else` block is also executed if the loop body is not run even once because, in that case also, the loop exits naturally and not due to `break`.

The `for` loop will not execute even once if the iterable is empty, and the `while` loop will not execute even once if the condition is `False` the first time through the loop.

## `pass` statement

When a `pass` statement is executed, nothing happens. It is just a null operation or a do-nothing statement. It is used as a placeholder when the syntax requires a statement, but you do not want to execute anything.

```python
if x >= 0:
  pass
else:
  x += 10
```

## `for` loop vs. `while` loop

- The `while` loop is a condition-controlled loop because the number of iterations of the loop is determined by the condition. The `for` loop is a collection-controlled loop since it iterates over a collection of things. It can be used as a counter-controlled loop also using the `range` function.

- The `while` loop is an indefinite loop because before the loop executes, we cannot always tell how many times it will execute. It runs indefinitely until some condition is met. The `for` loop is a definite loop because before the loop executes, we know exactly how many times it will execute. The number of times it iterates depends on the size of the collection.

- Use a `while` loop when you do not know in advance how many times to repeat the task, but you know when to stop repeating. Use a `for` loop when you have to iterate over a collection of things, i.e., when you want to perform an action on every item in a collection. You can also use a `for` loop when you have to repeat a task a fixed number of times.

- The `while` statement can be used to write both definite and indefinite loops, but `for` loop is specifically made for definite loops. So, whenever you know ahead of time how many times to iterate, use a for loop.

## The `enumerate()` function

You can generate the index and the corresponding value at the same time by using the `enumerate` function. This function takes in an iterable and returns an object which can be converted into a _list of tuples_ by using the _list_ function or can be used directly in a `for` loop.

```python
trip = ['Milan', 'Venice', 'Munich', 'Vienna', 'Budapest', 'Prague']
print(enumerate(trip)) # <enumerate object at 0x00000243E0FDA100>
print(list(enumerate(trip))) # [(0, 'Milan'), (1, 'Venice'), (2, 'Munich'), (3, 'Vienna'), (4, 'Budapest'), (5, 'Prague')]
```

By enclosing the object in the list function, we get a list of tuples where each tuple contains a count and an item returned by the list. The count starts with 0 by default. We can make it start from any other number instead of zero; for example, we can start it from 1.

```python
list(enumerate(trip,1))

# [(1, 'Milan'), (2, 'Venice'), (3, 'Munich'), (4, 'Vienna'), (5, 'Budapest'), (6, 'Prague')]

list(enumerate(trip,100))
# [(100, 'Milan'), (101, 'Venice'), (102, 'Munich'), (103, 'Vienna'), (104, 'Budapest'), (105, 'Prague')]

```

Now, let us use the `enumerate` function to display all the items of the list with their index number.

```python
for i, city in enumerate(trip, 1):
  print(f'Destination {i} -> {city}')

# Destination 1 -> Milan
# Destination 2 -> Venice
# Destination 3 -> Munich
# Destination 4 -> Vienna
# Destination 5 -> Budapest
# Destination 6 -> Prague
```

In each iteration, `enumerate` object gives a tuple which we are unpacking into the variables `i` and `city`. So, when you have a situation where you want to iterate over items of a sequence and also need the index number, you can use the `enumerate` function.

## The `zip()` function

The `zip()` function can be used to iterate over multiple sequences of the same length.

It takes multiple sequences and returns an object that gives us tuples from items that are at the same offsets in those sequences.

```python
names = ['Amit', 'John', 'Mark', 'Raj']
salaries = [2000, 3000, 2500, 3200]
cities = ['Delhi', 'Chennai', 'Delhi', 'Bangalore']
zip(names, cities, salaries) # <zip object at 0x0000019C90023940>
```

This `zip` function returns an iterable object, we need to enclose it in a _list_ to be able to see the _tuples_.

```python
list(zip(names, cities, salaries))

# [('Amit', 'Delhi', 2000), ('John', 'Chennai', 3000), ('Mark', 'Delhi', 2500), ('Raj', 'Bangalore', 3200)]
```

The following `for` loop iterates over the three lists `names, cities and salaries` by using the `zip` function.

```python
for name, city, salary in zip(names, cities, salaries):
  print(f'{name} posted in {city} with {salary}')
```
