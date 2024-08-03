# CHAPTER 17 - Lambda Expressions and Functional Programming

## Lambda expression

Apart from def statement, we have one more tool in Python that gives us a function object. It is called lambda expression. Here is an example of a lambda expression: `lambda x, y: x + y`

The function object produced by lambda expression is not given any name as it is done in the def statement. That is why these are also called anonymous (unnamed) functions. The `lambda` expression, `lambda x, y: x + y` is like a simple function that takes two arguments and returns the expression `x + y`. When we define a function using `def`, we have a name so we can call the function using the name, or we can send the name as an argument to another function, but `lambda` expression gives us a nameless function object, so now the question is how do we call it. Here is a way in which it can be called:

```python
(lambda x, y: x + y)(2, 3) # 5
```

Here is the syntax of a `lambda expression: lambda parameter1, parameter2, ……: expression`

The lambda keyword is followed by an optional parameter list; these parameters are not inside parentheses. After the parameters, we have a colon. This colon separates the parameter list from the body of the function. The body of the function here is limited to a single expression. When the function object returned by the `lambda` expression is called, code in the expression is evaluated and the value of the expression is returned. There is no explicit `return` keyword, the value of the expression is returned implicitly. So, when the `lambda` expression is executed, a function object is created and when that function object is called, the expression after the colon is evaluated and its value is returned.

`lambda` expressions are best suited for single use short functions as the function objects produced by them can be garbage collected after they have been used, unlike function objects produced by `def` statements.

There are some higher-order functions that are built-in like `max, min, sorted, map, filter`, and some are there in the standard library like `functools.reduce`. The `lambda` functions are often used in combination with these functions.

## Functional programming

Functional programming is a programming paradigm in which most of the work in a program is done using pure functions. A pure function is a function without any side effects; its return value is always determined by its input arguments, so it always returns the same output, given the same input. In Python, functional programming is supported by the higher-order functions `map, filter,` and `reduce`.

## The End
