# Chapter 1

## Item 1: Pythonic Thinking

- Check python version:
1. Via command line:
```python
    python3 --version
```

2. Via Python interpreter:
```python
    import sys
    print(sys.version)
```

## Item 2: PEP 8 - Style Guide for Python Code


1. Whitespace:
   - Use 4 spaces for indentation.
   - Lines should be less than 79 characters.
   - Additional lines of continued long expressions must be indented with 4 spaces.
   - In a file, functions and classes must be indented with 4 spaces.
   - In a class, methods must be seperated by one blank line.
   - In a dictionary: put no space between a key and colon, add single space after colon and value (if it fits in a single line.) i.e `{'key': 'value'}`
   - Put one space before and after the `=` sign. i.e `a = 5`.
   - For type annotations, put one space before and after the `:` sign. i.e `a: int = 5`.

2. Naming:
   - Functions, variables, classes, and modules should be in snake_case. i.e `my_function`.
   - Prefixed with `_` for internal use. i.e `_my_function`.
   - Prefixed with `__` for private use. i.e `__my_function`.
   - Capitalized name for classes. i.e `MyClass`.
   - Instance variables should be prefixed with `self.` i.e `self.my_variable`.
   - Class methods should use cls as the first argument. i.e `self.my_method(cls)`.
  
3. Expressions and Statements:
   - Use inline negations, i.e  `if a is not b` instead of `if not a is b`.
   - Don't check for empty containers using `len()`, use `if a:` instead. i.e.
        - instead of `if len(a) == 0:`, use `if not a`.
        - instead of `if len(a) != 0:`, use `if a`.
   - Use `is` instead of `==` for comparing objects.
        -  i.e instead of `if a == b`, use `if a is b`.
   - Avoid inline statements when not necessary.
   - Surround multiline statements with parantheses `()` instead of the `\` line continuation character.
    - Use `pass` as a placeholder for empty statements.
  
4. Imports:
   - Imports must be at the top of the file.
   - Always absolute imports are preferred. i.e. `from module import function`, instead of `import module.function`.
   - If relative imports are must, then use `from .module import function`.
   - Imports in order:
       - Standard library imports.
       - Third party imports.
       - Local imports.
   - Avoid using `from module import *`.

## Item 3: bytes and str character sequence

1. Byte strings:
    - Use `bytes` for binary data. Contains raw, unsigned 8-bit values.
            
    ```python
    >>> a = b'h\x65llo'
    >>> print(a)
    b'hello'
        
    >>> print(list(a))
    [104, 101, 108, 108, 111]

    # Convert byte to string
    >>> string = a.decode('utf-8')
    >>> print(string)
    'hello'
    ```
    - To read a binary file:
        - Use `open(filename, 'rb')`
        - Use `read()` to read the entire file.
        - Use `close()` to close the file.
    ```python
    with open('test.bin', 'wb') as f:
        f.write(b'hello')
    ```
2. Strings:
    - Use `str` for text data. Contains raw, Unicode characters.
    - Instances of strings contain Unicode characters.
            
    ```python
    >>> a = 'hello'
    >>> print(a)
    'hello'
        
    >>> print(list(a))
    ['h', 'e', 'l', 'l', 'o']
    ```

- String concatenation and comparision  is possible with same type of strings. i.e. bytes with bytes, and str with str.
  
    ```python
    >>> a = b'hello'    # bytes
    >>> b = 'world'     # str
    >>> print(a + b)
    b'helloworld'

    >>> print(a + b.encode('utf-8'))
    b'helloworld'

    # Addition of bytes with strings
    >>> print(a + b)
    Traceback (most recent call last):
    File "<stdin>", line 1, in <module>
    TypeError: can't concat str to bytes
    ```
    ```python
    # Convert bytes to str and add
    >>> print(a.decode('utf-8') + b)
    helloworld
    ```

    - To read a text file:
        - Use `open(filename, 'r')`
        - Use `read()` to read the entire file.
        - Use `close()` to close the file.
    ```python
    with open('test.txt', 'r') as f:
        print(f.read())
    ```


## Item 4: F-Strings over C-style string and `str.format()`

Instead of using C-style string and `str.format()`, use inbuilt- robust f strings to avoid type conversion incompatibilities and other issues that might occur. 


```python
shopping_list = [("milk", 0.77), ("eggs", 2.10), ("cheese", 2.8), ("bread", 1.30), ("butter", 1.8)]

>>> for i, (item, price) in enumerate(shopping_list):
        print(f"{i+1:<3}. {item:<10} -  € {price:.2f}")

1   milk       - €0.77
2   eggs       - €2.10
3   cheese     - €2.80
4   bread      - €1.20
5   butter     - €1.80
```

- f-strings are able to use `{var_name}` instead of `%` for formatting.
    - Use `{var_name:<width}` to left align the variable.
    - Use `{var_name:>width}` to right align the variable.
    - Use `{var_name:^width}` to center the variable.

More documentation can be found at [here](https://docs.python.org/3/reference/lexical_analysis.html#f-strings) and [here](https://docs.python.org/2/library/string.html#formatspec).


## Item 5: Helper functions instead of single complex functions

- The example below reads the red, green, blue and alpha values from a dictionary and returns zero, if the values in the dictionary are missing.
  
1. Without healper function:

```python
>>> incomplete_dict = {"red": ['220'], "green": [''], "blue": ['240'], "alpha" :['']}

>>> red = incomplete_dict.get("red", [''])[0] or 0
>>> red = int(red)
>>> green = incomplete_dict.get("green", [''])[0] or 0
>>> green = int(green)
>>> blue = incomplete_dict.get("blue", [''])[0] or 0
>>> blue = int(blue)
>>> alpha = incomplete_dict.get("alpha", [''])[0] or 0
>>> alpha = int(alpha)


>>> print(f"red: {red}")
red: 220
>>> print(f"green: {green}")
green: 0
>>> print(f"blue: {blue}")
blue: 240
>>> print(f"alpha: {alpha}")
alpha: 0
```

2. With helper function:

```python
>>> incomplete_dict = {"red": ['220'], "green": [''], "blue": ['240'], "alpha" :['']}

>>> def get_color_value(color_name, color_dict, default = 0):
        value = color_dict.get(color_name, [''])
        if value[0]:
            return int(value[0])
        return default
    

>>> red = get_color_value("red", incomplete_dict)
>>> green = get_color_value("green", incomplete_dict)
>>> blue = get_color_value("blue", incomplete_dict)
>>> alpha = get_color_value("alpha", incomplete_dict)

>>>  print(f"red: {red}")
red: 220
>>> print(f"green: {green}")
green: 0
>>> print(f"blue: {blue}")
blue: 240
>>> print(f"alpha: {alpha}")
alpha: 0
```
- Helper functions are advised to be used when the same process is carried out multiple times. Also helps to find bugs in the program, as the author has to focus on a function rather than searching all the variables.



