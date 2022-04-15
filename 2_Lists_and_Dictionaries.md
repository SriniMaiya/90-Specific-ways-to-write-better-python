## Item 11: Slice sequences

- Slicing: The basic slicing syntax for a list is, `somelist[start:end:step]`. 
    - Python indexing is start inclusive and end exclusive. 
    - Last value of the list can be indexed with `-1`
    - Python lists are backward indexing compatible too.
```python
a = ["a", "b", "c", "d", "e"]
print("Middle two:", a[1:3])
print("All but ends:", a[1:-1])
>>>
Middle two: ['b', 'c']
All but ends: ['b', 'c', 'd']
```
```python
a[:] # All
>>>
['a', 'b', 'c', 'd', 'e']
a[1:] # All but first
>>>
['b', 'c', 'd', 'e']
a[:-1] # All but last
>>>
['a', 'b', 'c', 'd']
a[::2] # All but every other
>>>
['a', 'c', 'e']
a[::-1] # All but reversed
>>>
['e', 'd', 'c', 'b', 'a']
a[::-2] # All but every other reversed
>>>
['e', 'c', 'a']
a[1::2] # All but first and every other
>>>
['b', 'd']

```