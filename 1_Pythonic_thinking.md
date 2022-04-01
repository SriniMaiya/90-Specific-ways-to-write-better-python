## Chapter 1

### Item 1: Pythonic Thinking

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

### Item 2: PEP 8 - Style Guide for Python Code

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
  
### Item 3: bytes and str character sequence

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




    