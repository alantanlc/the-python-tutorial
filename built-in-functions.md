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

### chr(_i_)
Return the string representating a character whose Unicode code point is the integer i. For example, `chr(97)` returns the string `'a'`, while `chr(8364)` returns the string `'€'`. This is the inverse of [ord()]().

The valid range for the argument is from 0 through 1,114,111 (0x10FFFF in base 16). [ValueError()]() will be raised if _i_ is outside that range.

### enumerate(_iterable, start=0_)
Return an enumerate object. _iterable_ must be a sequence, an [iterator()](), or some other object which supports iteration. The [\_\_next\_\_()]() method of the iterator returned by [enumerate()]() returns a tuple containing a count (from _start_ which defaults to 0) and the values obtained from iterating over _iterable_.
```python
>>> seasons = ['Spring', 'Summer', 'Fall', 'Winter']
>>> list(enumerate(seasons))
[(0, 'Spring'), (1, 'Summer'), (2, 'Fall'), (3, 'Winter')]
>>> list(enumerate(seasons, start=1))
[(1, 'Spring'), (2, 'Summer'), (3, 'Fall'), (4, 'Winter')]
```
Equivalent to:
```python
def enumerate(sequence, start=0):
  n = start
  for elem in sequence:
    yield n, elem
    n += 1
```

### filter(_function, iterable_)
Construct an iterator from those elements of iterable for which _function_ returns true. _iterable_ may be either a sequence, a container which supports iteration, or an iterator. If _function_ is None, the identity function is assumed, that is, all elements of _iterable_ that are false are removed.

Note that `filter(function, iterable)` is equivalent to the generator expression `(item for item in iterable if function(item))` if function is not `None` and `(item for item in iterable if item)` if function is `None`.

See [itertools.filterfalse()]() for the complementary function that returns elements of _iterable_ for which _function_ returns false.

### _class_ float([_x_])
Return a floating point number constructed from a number or string x.

If the argument is a string, it should contain a decimal number, optionally preceded by a sign, and optionally embedded in whitespace. The optional sign may be `'+'` or `'-'`; a `'+'` sign has no effect on the value produced. The argument may also be a string representing a NaN (not-a-number), or a positive or negative inifinity. More precisely, the input must conform to the following grammar after leading and trailing whitespace characters are removed:
```python
sign            ::=   "+" | "-"
infinity        ::=   "Infinity" | "inf"
nan             ::=   "nan"
numeric_value   ::=   floatnumber | infinity | nan
numeric_string  ::=   [sign] numeric_value
```
Here `floatnumber` is the form of a Python floating-point literal, described in [Floating point literals](). Case is not significant, so, for example, "inf", "Inf", "INFINITY" and "iNfINity" are all acceptable spellings for positive infinity.

Otherwise, if the argument is an integer or a floating point number, a floating point number with the same value (within Python's floating point precision) is returned. If the argument is outside the range of a Python float, an [OverflowError]() will be raised.

For a general Python object `x`, `float(x)` delegates to `x.__float__()`. If `__float__()` is not defined then it falls back to [\_\_index\_\_()]().

If no argument is given, `0.0` is returned.

Examples:
```python
>>> float('+1.23')
1.23
>>> float('   -12345\n')
-12345.0
>>> float('1e-003')
0.001
>>> float('+1E6')
1000000.0
>>> float('-Infinity')
-inf
```

The float type is described in [Numeric Types -- int, float, complex]().

### hash(_object_)
Return the hash value of the object (if it has one). Hash values are integers. They are used to quickly compare dictionary keys during a dictionary lookup. Numberic values that compare equal have the same hash value (even if they are of different types, as is the case for 1 and 1.0).
> Note: For objects with custom `[\_\_hash\_\_()]()` methods, note that `[hash]()` truncates the return value based on the bit width of the host machine. See `[\_\_hash\_\_()]()` for details
