# Looping
Most things are, or can be made, iterable. 
An `iterable` is anything on which you can get an `iterator`.
An `iterator` is something that responds to `next()` to give you the next value.
Calling `next` on an empty iterator raises a `StopIteration` exception. 

While it's not possible to iterate backwards, you can create two iterators on the same iterable and run them independently.
To obtain all iterable values at once, call `list()` (or `set()` or `tuple()`).

### Iterating dicts
`for k in d` assigns keys to `k`. 
To get only values: `for v in d.values()`.
To get both: `for k,v in d.items()`.

### Tricks
To execute something after normally completing the iteration: 
```python
for ...
    ...
else:
    print('finished')
```
