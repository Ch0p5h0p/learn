# Control Structures

Control structures are things that allow you to control which things your program does and doesn't do, and how many times to do them. Before we talk about control structures, we need to talk more about booleans, which control them.

We have X comparison operators:

| Name | Symbol |
| --- | --- |
| Greater than | `>` |
| Less than | `<` |
| Greater than or equal to | `>=` |
| Less than or equal to | `<=` |
| Equal to | `==` |
| Not equal to | `!=` |
| And | `and` |
| Or | `or` |
| Not | `not` |
| In | `in` |
| Is | `is` |


Each comparison operator evaluates to a boolean value.

### Equality operators
`<`, `>`, `<=`, and `>=` work exactly as they do in math. `a < b` returns `True` if `a` is less than b, otherwise it returns `False`. An operator that is very important to remember is `==`. It is NOT the same as `=`. `=` is for assignment, `==` is for comparison.

### Logical operators
The logical operators are `and`, `or`, and `not`. The `and` operator is `True` ONLY if both sides evaluate to `True`. NOT if both sides are `False`. The `or` operator returns `True` if one side evaluates to `True`. Note that this evaluates to `True` if both sides are `True` as well. `not` is what we call a *unary operator*. So far we've been talking about binary operators, which are operators that take two parameters. `not` is a unary operator, meaning it only takes one parameter. We only have `not a`, and something like `a not b` will throw an error.

### Python-specific operators
The two Python-specific operators we'll be talking about are `is` and `in`. `is` is a strange mutation of `==`. Doing `a is b` will operate basically the same as if you did `a == b`. The difference is that `==` checks the data in something, while `is` checks the identity as well. `is` will check memory to see if two variables are the same thing in memory. `in` is used for container types such as lists, tuples, and dictionaries to check if they contain a specific value. `a in l` checks if a exists in l.

## Control Structures (for real this time)
There are X main control structures you need to know:
- If
- While loop
- For loop

### If
An if statement is simply a conditional. Before we talk about these, though, we need to talk about indentation

#### Indentation
In programming, you have something called a *scope*. Scope is a section of code that only has access to said scope, and the scope can be manipulated. In Python, we denote scope with indentations. In Python, if the next line is indented at the same level as the previous, they're in the same scope. These come in many different forms. It can either be tabs or spaces. Generally accepted spacing sizes if you use spaces are 2 spaces and 4 spaces. I personally prefer to use tabs. You probably should also use tabs. They're simpler, and most IDEs will prevent any sort of mixing between tabs and spaces and will handle other errors from indentation

#### Ok, back to if statements
The way you can define an if statement is like so:
```python
if condition:
  body
```

Here's an example one with multiple levels:
```python
if a >= b:
  print("a is greater than or equal to b!")
  if a == b:
    print("Oh wait nope just equal")
```

If statements can also have a few other clauses: `else` and `elseif`. Let's start with `else`.

`else` simply runs if the if statement's condition fails to be met. For example:
```python
if a > b:
  print("a is greater than b!")
else:
  print("a is not greater than b")
```

`elseif` allows chained conditions. It effectively operates as another if statement in a chain. Here's an example:
```python
if a == b:
  print("a equals b")
elseif a < b:
  print("a is less than b")
elseif a > b:
  print("a is greater than b")
else:
  print("something weird happened idk")
```

When you construct a chain, it should have the most specific condition first. This is because in an elseif chain, (an if statement with two or more `elseif` clauses), when an `elseif` clause hits, it will terminate the chain after executing the body.

You can also write if statements in-line to select between specific values. For example, you can write:
```python
print("hello" if entering else "goodbye")
```

### While loops
A while loop is a structure that executes its body until the provided condition becomes false. For example, we can make the following counting loop:
```python
a:int = 10
while a > 0:
  a -= 1
  print("a is now: " + a) # note: + can be used to add a value to a string through concatenation
```

This while loop will count down from 10 until `a` becomes 0, then it stops. You can break out of a while loop by using `break`. For example, we can remake our previous counting loop like so:
```python
a:int 10

# while True is an infinite loop
while True:
  a -= 1
  if a <= 0:
    break
```

Another keyword that is important is `continue`. `continue` skips the remainder of the current iteration and starts the next one.

### For loops
A for loop is similar to a while loop, except instead of a condition, we provide a series of values to apply the iteration to. Before I dive into for loops, here are two ways of writing them:
```python
# method 1
for i in range(0,10):
  print(i)

# method 2
for i in [0,5,4,7]:
  print(i)
```

*note: `i` is standard as a variable in for loops, but can be replaced with any variable name*

*also note that `range()`'s domain is [a,b), meaning it includes a but excludes b. It can be written with one parameter instead, which makes the initial value default to 0, giving it a domain of [0,a)*

Method 1 declares a range to be used. Method 2 declares a list of values to be used. Method 1 will output the following:
```
0
1
2
3
4
5
6
7
8
9
```

While method 2 will output the following:
```
0
5
4
7
```

The general template for a for loop is this:
```python
for variable in iterable:
  body
```

Where iterable means any structure (list, tuple, etc) that hold many values and returns them one at a time. The variable will contain the value of the current item for the iteration you're on, and is only valid in the scope of the loop.

## List comprehensions
Control structures can be used in sometihng known as a list comprehension, which is an efficient way for creating large lists. For example, here's how we would generate a list of the square of all the numbers divisible by 3 from 1 to 100:
```python
l:list[int] = [ i*i for i in range(1,101) if i % 3 == 0 ]
```

*in Python, % means modulus, which is the remainder after division. If the remainder is zero, a number is perfectly divisible.*

This sets `l` equal to this value:
```python
[9, 36, 81, 144, 225, 324, 441, 576, 729, 900, 1089, 1296, 1521, 1764, 2025, 2304, 2601, 2916, 3249, 3600, 3969, 4356, 4761, 5184, 5625, 6084, 6561, 7056, 7569, 8100, 8649, 9216, 9801]
```

## Ending
Now we know how to control our program and do fun things! As an excercise, use the `input()` function to make a number guessing game. You can even make it multiple rounds by using a list if you want. `input()` takes in a string as the sole parameter, then waits for the user to enter a value and press enter before using it. For example, `a:str = input("what's your name? ")` would wait for me to enter a value (hopefully my name) and then store it in `a`.

[Table of Contents](/learn/pages/ToC.md)
