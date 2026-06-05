---
layout: page
title: "Variables and Types"
next_url: "/pages/python/control_structures.html"
next_title: "Control Structures"
toc_url: "/pages/ToC.html"
prev_url: "/pages/python/hello_world.html"
prev_title: "Hello, World!"
---

# Variables and Types

As of writing this, I'm guessing you have enough understanding of math to understand what the mathematical expression `x=2` means. If you don't for some reason, `x` in this case is a variable. The expression `x=5` means that `x` is assigned to be 5.

This is a staple of every programming language. In Python, their declaration is just as simple:
```python
x=5
```

*(you can put spaces between the value and the `=`, btw)*

and now `x` is set to 5. It's that easy! Except I'm going to make it harder, because Python hides a lot of this from you :)

## Types
In programming, we have a set of generally defined types. The most basic of these types (generally known as the *integral datatypes*) are as follows:


| Name | Common Shortening | Description |
| --- | --- | --- |
| Integer | `int` | Any whole number, such as 1, 4, 8, or 12,563 |
| Float | `float` | A floating-point number, such as 1.45, 19.64, or 2.00001 |
| Double | `double` | Sometimes `float` variables don't have enough precision. So we use `double` variables, which are twice the precision of `float` variables |
| Character | `char` | any singular character, such as t, Z, P, or d |
| Boolean | `bool`, `boolean` | a value that is either true or false. In many languages, they correspond to 1 (true) and 0 (false) |

Python programmers don't usually have to worry about this. If you plan to stick with just Python, you don't really have to worry about this as much either. But if you DO plan on progressing past Python, then the following part is for you. Otherwise, go ahead and jump [here](#using-variables)

## Type Annotations
In Python, we can annotate the types of variables when we define them. It's important to note that the interpreter DOES NOT CHECK the validity of annotations. For example, if you annotate a float as an integer, the interpreter doesn't care. So it's YOUR problem to ensure your annotations are valid.

That being said, these are the following valid types for Python:


| Type | Description |
| --- | --- |
| `int` | Exactly the same as the integral integer type earlier |
| `float` | In Python, the integral `float` and `double` types are combined into simply `float`
| `str` | This is a departure from integral types. `str` represents a string, which is a string of any length of characters, such as "Hello" |
| `bool` | The same as the integral boolean type earlier |
| `bytes` | A raw bytes object, written in binary (prefixed with 0b) or hexcode (prefixed with 0x) |
| `None` | Not as useful for variables, but important to note for later. Represents the absence of a type |

To annotate the type of a variable, we turn this:
```python
x=5
```

into this:
```python
x:int=5
```

Here are examples of each type:
```python
# integer
a: int = 5

# float
b: float = 0.14

# string
c: str = "Hello, world!"

# boolean
d: bool = True

# bytes
e: bytes = 0x5F
```

## Variables vs Literals
A literal is simply a literal instance of a type. If that makes no sense or feels recursive, let me give you an example to make it make sense:

1 is an integer literal.

See? 1 is LITERALLY an integer. Similarly, `True` is a boolean literal, `0.2` is a float literal, and `"Hello"` is a string literal. So to define a variable, we first have to assign it to a literal.

## Using Variables
All types can be used in print statements simply by putting them into the parenthesis instead of a string. Simply `print(x)`.

## Other types
There are more types beyond the "integral" types Python provides us. These are a few:


| Type | Shortening | Description |
| --- | --- | --- |
| List | `list` | a collection of any number of any type of values |
| Dictionary | `dict` | a table to reference items by specified keys |
| Tuple | `tuple` | similar to a list, but immutable |

### Lists
List are defined like so:
```python
myList = [5, "hello", 0.1, True]
```
You can access any element of an already defined list like this:
```python
myList[1]
```
That line would return "hello". Wait, what? 1 isn't the first item in the list? Nope! Actually, the first item in a list is at `myList[0]`. This is called zero-based indexing.

If you want to specify the types a list contains, you can annotate like so:
```python
first_ten: list[int] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

### Dictionaries
Dictionaries are defined like so:
```python
user = {
  "id" : "1b345a",
  "name": "bob",
  "occupation": "professional coffee drinker"
}
```
And can be accessed like this:
```python
user["id"]
```
They can be annotated similarly to lists:
```python
user: dict[str, str] = {
  "id" : "12345",
  "name": "bob",
  "occupation": "professional coffee drinker"
}
```

### Tuples
Tuples are basically the same as lists, except they're defined using parenthesis instead of square brackets. They're accessed the same way, and are annotated like so:
```python
greetings: tuple[str] = ("hello", "greetings", "nice to meet you")
```

## Good Practice
At this point, it's important I talk about good practice. Lists aren't a very common feature. More common are arrays, which are very similar to lists, except they only allow one singular type to be a part of them. For instance, you can't have an array with both strings and integers. You can only have one type present.

Another important thing is that variables can't change type in other languages. In Python, it's perfectly legal to do this:
```
x=5
x="hello"
```
which would reassign x from an integer to a string. This isn't allowed in most other languages due to the high likelihood of bugs coming from it. Same with lists having many types. It's generally a good idea to maintain that lists only have one type and variables remain the same type.

## Ending
Whew, that was long! With any luck, this should be the longest section in the Python chapter.
