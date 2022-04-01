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

### Item 2: PEP 8 - Style Guide for Python Code:

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
   - Don't check for empty containers using `len()`, use `if a:` instead. 
  
        i.e instead of `if len(a) == 0:` use `if a:`.