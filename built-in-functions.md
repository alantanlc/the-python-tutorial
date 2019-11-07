# Built-in Functions

The Python interpreter has a number of functions and types built into it that are always available.

### abs(_x_)
Return the absolute value of a number. The argument may be an integer or a floating number. If the argument is a complex number, its magnitude is returned. If x defines [\_\_abs\_\_()](), `abs(x)` returns `x.__abs__()`.

### all(_iterable_)
Return `True` if all elements of the _iterable_ are true (or if the iterable is empty). Equivalent to:
```python
def all(iterable):
  for element in iterable:
    if not element:
      return False
  return True
```

### any(_iterable_)
Return `True` if any element of the _iterable_ is true. If the iterable is empty, return `False`. Equivalent to:
```python
def any(iterable):
  for element in iterable:
    if element:
      return True
  return False
```

### ascii(_object_)
As [repr()](), return a string containing a printable representation of an object, but escape the non-ASCII characters in the string returned by [repr()]() using `\x`, `\u`, or `\U` escapes. This generates a string similar to that returned by [repr()]() in Python 2.

### bin(_x_)
Convert an integer number to a binary string prefixed with "0b". The result is a valid Python expression. If x is not a Python [int]() object, it has to define an [\_\_index\_\_()]() method that returns an integer. Some examples:
```python
>>> bin(3)
'ob11'
>>> bin(-10)
'-0b1010'
```
If prefix "0b" is desired or not, you can use either of the following ways.
```python
>>> format(14, '#b'), format(14, 'b')
('0b1110', '1110')
>>> f'{14:#b}', f'{14:b}'
('0b1110', '1110')
```
See also [format()]() for more information
