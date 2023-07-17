# Modern Python Best Practices
## Inspired by James Murphy's _25 nooby Python habits you need to ditch_ at https://www.youtube.com/watch?v=qUeud6DvOWI&t=3s, with a few additions

### Use f-strings for interpolation

    f'Text {name} text'

### Use `with` for resources with their own context managers

    with open (filename) as file:
        file.write("something\n")

### `except` clauses should include an exception class

    except Exception:
    except ValueError:

### Functions or methods with default _mutable_ arguments

    def append(n, l=None):
        if l is None:
            l = []
        l.append(n)
        return l

### Comprehensions

    list_comp = [x*x for x in range(10)}
    dict_comp = {i: i * i for i in range(10)}
    set_comp  = {i%3 for i in range(10)}
    gen_comp  = (2*x+5 for x in range(10))

### Use `isinstance()` rather than `type(p)` most of the time

    isinstance(p, tuple)

### Use `is` rather than == when you need to explicitly test for `None`, `True`, or `False` values

    if x is None:
        pass
    if x is True:
        pass
    if x is False:
        pass

### Not using `bool(x)` and `len(x)` in tests

    if x:
        pass

### Not using `range(len(a))` or explicit index management

    for value in a:
        pass
    for index, value in enumerate(a):
        pass
    for a_value, b_value in zip(a, b):
        pass
    for index, (a_value, b_value) in enumerate(zip(a, b)):
        pass

### Not using `for key in d.keys():`

    for key in d:
        pass

### Modifying a `dict`'s keys while looping over it

    for key in list(d):
        pass

### Updating a `dict`'s keys from another iterable

    iterable_key_value_pairs = ... # another dict or any iterable object producing `(key, value)` pairs
    d.update(iterable_key_value_pairs)

### Looping over keys and values in a `dict`

    for key, value in d.items():
        pass

### `tuple` unpacking

    x, y = my_tuple

### Calculate time interval

    start = time.perf_counter()
    time.sleep(1)
    end = time.perf_counter()
    print (end - start)

### Logging

    def logging():
        logging.debug("debug info")
        logging.info("just some info")
        logging.error("uh oh")
    def main():
        level = logging.DEBUG
        fmt = '[%(levelname)s] %(asctime)s - %(message)s'
        logging.basicConfig(level=level, format=fmt)

### Use `numpy` for bulk numerical data analysis (and `pandas` for more general bulk data analysis)

    import numpy as np
    def f():
        x = np.arange(100)
        y = np.arange(100)
        s = x + y

### Follow PEP8 styles

See https://peps.python.org/pep-0008/

### Use augmented assignment when applying an operator to modify an existing variable or mutable object

    i += 1
    x *= C
    set_a &= set_b

### Represent arbitrarily high or low values without explicit numbers

    float('inf')
    float('-inf')
    import math
    math.inf # positive infinite integer
    -math.inf # negative infinite integer
    Decimal('Infinity')
    Decimal('-Infinity')
    np_positive_infinity = np.inf
    np_negative_infinity = -np.inf
    math.isinf(np_positive_infinity)
    math.isinf(np_negative_infinity)
