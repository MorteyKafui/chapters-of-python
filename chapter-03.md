# CHAPTER 3 - List and Tuples

Lists are ordered collections of items. They can be considered similar to arrays in other languages. They are more flexible and powerful as they do not have fixed sizes and can store elements of different types.

## Creating A List

There are different ways to create a list in Python.

- Using square brackets

```python
fruits = ["apple","mango","banana"]
print(type(fruits))
```

- Using the built-in list() function in Python

```python
numbers = list([1,2,3,4,5,6])
print(type(numbers))
```

Also a list can have elements of different data types.

```python
mixed_list = [10, True, "red", "blue", None]
```

A list can contain another list.

```python
list_in_list = [[1, 2, 3, 4], ["black", "white"], True]
print(list_in_list)
```

Although lists allow mixed types, they are often used to store values of the same type. They are commonly used to represent collections of similar items, such as a list of names or a list of numbers. By storing values of the same type in a list, we can conveniently perform the same operation on all the elements of a particular list.

Values in a list need not be unique; it can have duplicate values. This means that the same value can appear multiple times at different positions in the list.

> NB: A list is a referential data structure, which means that it stores references to its elements.

```python
names = ["Bob", "Tim", "Tom"]

```

The list `names` refers to the list object and the list object stores references to different objects that represents the elements of the list. So, although we generally say that a list contains elements, it technically contains references to those elements.

The list type is mutable; this is the first mutable type that we are discussing. ‘Mutable’ means that an object of type list can be changed, and its contents can be altered. You can add new elements or delete/overwrite existing elements from the list object. This is why a list can dynamically contract or expand at runtime; its size is not fixed. The interpreter dynamically allocates more memory when required and also dynamically releases the memory no longer required by the list.

## Accessing Individual Elements of a List by Indexing

The elements of a list can be accessed by writing
integer index values enclosed in square brackets.
Like strings, lists also use zero-based indexing.

If `L` is the name of the list, then to access the first element, we write `L[0]`; for the second element L[1], and so on. A list of size n has elements indexed from `0` to `n-1`. As in strings, we can also give negative index values to index backward. So, `L[-1]` represents the last element, `L[-2]` the second last element, and so on. For a list of length 6, indices `0,1,2,3,4,5` and `-1,-2,-3,-4,-5,-6` are valid indices. Any integer less than -1 or more than 5 will be invalid. If you try to access a list element at an invalid index, the interpreter will raise an `IndexError`.

```python
numbers = [10, 20, 30, 40, 50, 60]
numbers[0] # prints the first element
numbers[-1] # prints the last element
numbers[10] # IndexError
```

## Getting Parts of a List By Slicing

We can extract a portion of the list by slicing. The slice operations that we saw for strings work for lists also in the same way. Slicing a list gives us a part of the list as a new list object. As in strings, we can get a slice of the list by specifying indices separated by colons inside square brackets.

```python
num_list = [10, 20, 30, 40, 50, 60, 70, 80]

num_list[2:7] # Gives a list that contains elements from index 2 to index 6
num_list[2,77] # Gives a list that contains elements from index 2 to index 10 (No IndexError)
num_list[:5] # Gives a list that contains elements from index 0 to index 4 (first 5 elements)
num_list[5:] # Gives a list that contains elements from index 5 to index 10
num_list[-5:] # Gives a list that contains elements from index -5 to index 10 (last 5 elements)
num_list[2:9:2] # Gives a list that contains every second element from index 2 to index 8
num_list[::2] # Gives a list that contains every second element starting from first index till last index
num_list[:] # Gives a list that is an exact copy of the list num_list
num_list[::-1] # Gives a list that is the reverse of the list num_list

```

If the first number inside the square brackets is omitted, it is considered zero; if the second is omitted, it is considered the last index. The third number represents the step and is optional; if it is omitted, it is considered `1`. The slice `num_list[:]` gives an exact copy of the list, and the slice `num_list[::-1]` gives the reverse of the list.

## Changing an Item in a List by Index Assignment

Since lists are mutable, it is possible to change a list object in-place. We can change any element in the list by assigning it to an index.

```python
nums = [10, 20, 30]
nums[0] = 100
print(nums)
```

## Changing a portion of the List by Slice Assignment

You can modify portions of the list by assigning them to slices. When a list slice is used on the left side of an assignment, the range specified in the slice will be replaced by what is on the right-hand side.

```python
nums = [1, 2, 3, 4, 5, 6, 7]
nums[2:5] = [0, 9, 6]
```

## List Methods

- The `append()` method adds a single item at the end of the list, and it returns `None`.

  ```python
  nums = [10, 20, 30, 40]
  nums.append(60)
  ```

- The `insert()` method adds a new item at a particular index in the list.
  ```python
  nums = [10, 20, 30, 40, 50, 60]
  nums.insert(2, 100)
  ```
- The `extend()` method adds multiple items at the end of the list.

  ```python
  nums = [10, 20, 30]
  nums.extend([40, 50, 60])
  ```

- The `pop()` method removes an item from the list and also gets/ returns the removed item.
  ```python
  nums = [10, 20, 30, 40]
  nums.pop(2) # removes and returns the element at index 2 in the list
  nums.pop() # reomves and returns the last element of the list
  ```
  > If we do not specify any index as an argument, then this method removes and returns the last element of the list. So, `pop()` without any argument is the same as `pop(-1)`.

The object returned by pop is generally assigned to a variable so that it can be used later. If the returned object is not assigned to any variable, then the returned object ceases to exist, and the memory occupied by it is reclaimed by the interpreter.

- The `remove()` method removes an element from the list, if you don't know its index in the list.

`L.remove(x)` will remove the first occurrence of item x from the list `L`, and it returns None. If x is not found in the list, then it raises `ValueError`.

```python
nums = [10, 20, 30, 40]
nums.remove(20)
```

`nums.remove(20)` removes the first occurrence of item 20 from the list. If there are multiple occurrences of the item and you want to remove all occurrences, you can use a loop or a list comprehension.

- The `clear()` method will remove all the items from the list, making it empty.

```python
nums = [10, 20, 30]
nums.clear() # []
```

- The `sort()` method is used to sort the elements of a list. It sorts the list in-place, which means that it will change your list object. The elements are sorted in ascending order, i.e., they are arranged from smallest to largest. If the elements are strings, they are sorted according to their ASCII values. This method returns `None`.

```python
nums = [1, 2, 3, 4, 5]
nums.sort()
```

To change the sorting order, add the argument `reverse=True`

```python
nums = [1, 2, 3, 4, 5]
nums.sort(reverse=True)
```

The numbers are now sorted from largest to smallest.

- The `reverse()` method reverses the order of the elements of the list in=place. It returns `None`.

```python
nums = [1, 2, 3, 4, 5]
nums.reverse()
```

## Built-in functions used on lists

- `len(list)`: Returns the size of the list.
- `min(list)`: Returns the smallest value of the list.
- `max(list)`: Returns the largest value of the list.
- `sum(list)`: Returns the sum of all the elements of the list if the elements are of numeric type.

## Tuples

Tuples are ordered sequences of elements, but they are
immutable, which means that once a tuple is defined, it cannot be changed.

```python
names = ("bob", "tim", "tom")
nums = (1, 2, 5)
() # empty tuple
(2, ) # unit tuple

```

## Tuple packing and unpacking

```python
employee = ('Raj', 20, 'Delhi', 15000)
name, age, city, salary = employee

```

## The End
