# Basics
## Looping
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
## Dictionaries
Since 3.7, dicts maintain the insertion order of entries.
The `globals()` and `locals()` functions return dicts of what lives in those scopes. 
The `.__dict__` special attribute stores the attributes of classes and objects. 
Dict keys must be **hashable**  (i.e. immutable) and **unique**.

### Constructing dicts
Using `dict()` you can provide the following args:
```python
dict()
dict(**kwargs)
dict(mapping, **kwargs)
dict(iterable, **kwargs)
dict( zip(keylist, valuelist) )

# Zipping
dict.fromkeys( keyiterable, value='default' )

# With comprehensions
squares = {i: i**2 for i in range(1,10)}
```

### Accessing
Safe access: `d.get(key, default=None)`. 
Values: `d.values()`.
Keys: `d.keys()`.
Entries: `d.items()`.

### Modifying
Get a value if a key is present, else give that key a default value and then return it: `value = d.setdefault(key, default='bla')`.

Merge another dict or iterable: `d.update(other)`.

Remove a key and get its value (or a default if key is absent): `d.pop(key, 'default')`. A straight delete is done with: `del mydict[key]`.

Remove the last inserted entry: `k,v = d.popitem()`. Errors if the dict is empty. 

Remove all entries: `d.clear()`.

### Operators
Test membership with `in` and `not in`. Test for equality of entries with `d1 == d2`. 

Create a union of 2 dicts: `d1 | d2`. An augmented union assigns the result to the LHS: `d1 |= d2`. 

### Built-ins
* `all()`, `any()`: true if all/any items in an iterable are truthy, e.g. test if any values are zero: `all(d.values())`. 
* `len()`: number of entries.
* `min()`, `max()`: find min/max values of keys or values. 
* `sorted()`: by key or value. E.g. `dict( sorted(mydict.items(), key=lambda e: e[1], reverse=True) )`. 
* `sum()`: usually for values, `sum(d.values())`. 

### Special dicts from `collections`
`OrderedDict`, remembers the order of items, defined by insertion order of keys. But normal dicts do this now (from 3.7).


`Counter`, counts elements in an iterable, returning results as `{ e1: n1, e2: n2 }`. 
Results are sorted ascending by default, which is **useful for building rankings**.

`defaultdict` creates a new key and default value when you try to access/modify a missing key:
```python
depts = defaultdict(list)
for dep, emp in employees:
    deps[dep].append(emp) # new key with empy list as a value, if 'emp' not present
```

