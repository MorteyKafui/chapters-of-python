# CHAPTER 5 - Conditional Statements

The control flow of a program is the order in which the code written in the program executes. Normally, the program executes from top to bottom with one statement executed at a time. This is called sequential control. All the programs we have written have been executed this way: top to bottom and one statement at a time. This normal flow of control is changed by control structures, which can be either selection control structures or iterative control structures.

In Python, selection is supported by the `if statement`, and iteration is supported by the `while statement and for statement`. The `if
statement` is a conditional statement, meaning we can use it to process our code conditionally. The two iterative structures, `while statement and for statement` are called _loops_ as they are used to
repeatedly execute a section of code.

## if Statement

As in most other languages, in Python also, decision making or conditional execution is done with the help of an `if` statement. By using an `if` statement, you can
make your program behave differently in different situations. It gives your program the ability to make decisions and perform actions based on those decisions. When you need to execute some statements only if a certain condition holds, you can use an `if` statement.

```python
if test_expression:
  statement1
  statement2
  statement3

```

We have the `if` keyword followed by a test expression, and then we have a colon. The test expression is a Boolean expression, and therefore, it can be either `True` or `False`; it is often called the if condition. After the colon, we have the statement block, which will be executed when the test expression is `True`. Each statement in this block should be indented by the same length from the if line. We have seen earlier that Python uses indentation to identify a block. If the test expression evaluates to `True`, the statements inside the block will be executed, and then the next statement after the `if` statement will be executed. If the test expression evaluates to `False`,
the statements inside the block will be skipped, and the next statement will be executed.

A _block_ is also called a suite in Python, and it is a group of statements grouped together through indentation. To specify the boundaries of a block, Python uses indentation instead of curly braces or some keywords like begin or end that are used in other languages.

You can have any number of statements inside a block; there is no limit, but there should be at least one statement. The colon marks the start of the statement block, and the first unindented statement marks the end of the block. The block finishes when the indentation decreases. The exact amount of indent may vary, but the indentation should be consistent. The recommended indent is _4 spaces_. It is not a good idea to use tabs or mix tabs and spaces while indenting. Mixing tabs with spaces can result in errors, even though it might look correct on the screen.

You can combine multiple conditions using the three logical operators `and`, `or`, and `not`.

To check whether a value is present in a list, tuple, string, or dictionary, we can use the `in` and `not in` operators.

## else clause in `if` statement

In the `if` statement, you can also add an `else` clause in which you can write the statements that you want to be executed when the test expression is `False`.

The `else` keyword is followed by a colon and should be aligned with the keyword `if`. All the statements in the `else` block should be indented by the same amount. If the test expression is `True`, then the `if` block is executed; otherwise, the `else` block is executed.

```python
if test_expression:
  statement1
  statement2
  statement3
else:
  statement1
  statement2

```

## Nested `if` statements

`if` statements can be nested, which means that you can have an `if` statement inside another `if` statement. Inside the `if` block or the `else` block, we can have any type of Python statement; it can be an `if` statement also.

```python
if test_expression:
  statementA
  statementB

  if test_expression:
    statement1
    statement2
  else:
    statement0
else:
  statementY

  if test_expression:
    statement4
    statement5
  else:
    statementX
```

## Multiway selection by using `elif` clause

This structure is like an `else-if` chain or `else-if` ladder; it is used when we have multiple mutually exclusive conditions.

```python
if test_expression:
  statement1
  statement2
elif test_expression:
  statement3
  statement4
elif test_expression:
  statement5
  statement6
else:
  statementZ
```

Each `elif` keyword should align with the `if` keyword and the final `else` keyword. The keyword `elif` is just a shortcut for `else if`.

The `elif` clause helps in multiway selection and reduces the amount of indentation that is to be done when we use the nested if `else` statements. The working of this construct is simple: each condition is checked in order; if the first condition is `True`, the statement block
under it is executed, and other conditions are not checked. If the first condition is `False`, the second is checked; if the second is `False`, the third is checked, and so on. If any of them is `True`, the block under it
executes, and the control comes out of the whole `if` statement. The final else block will be executed when none of the conditions is `True`, so it acts as the default case.

## `if else` operator (ternary operator)

We know that unary operators operate on one operand, and binary operators act on two operands. The operator that we are going to see now is a ternary operator, as it acts on three operands. Here is what the if-else operator looks like with its three operands.

```python
expression1 if test_condition else expression2
```

The test_condition or the condition is evaluated, and if it is `True`, the left expression is evaluated and its value is the value of the whole expression, and if the condition is `False`, then the right expression is evaluated and its value is the value of the whole
expression. So, this operator checks the condition and then returns the value of either of the two expressions, depending on the truth value of the condition. The condition will always be evaluated, while only one of the two expressions will be evaluated.

```python
remarks = "Pass" if marks >=50 else "Fail"
discount = 5 if items < 10 else 15
```

## The End
