the purpose of `with ... as` is to automatically handle setup and cleanup of an object. It guarentees the clean up runs even if there is an exception in between (something like try with resources in java)

to safely open a file for reading we use
```python
file = open("data.txt", "r")

try:
    content = file.read()
    print(content)
finally:
    file.close()
```

Easier to express it using `with ... as`

```python
with open("data.txt") as file:
  content = file.read()
  print(content)
```

it can be roughly translated as below

```python
manager = open("data.txt", "r")

file = manager.__enter__()

try:
    print(file.read())
finally:
    manager.__exit__(None, None, None)
```

This can be achieved using special dunder methods enter and exit in a class

* `__enter__(self)`: returns an object that can be assigned to variable after `as`
* `__exit__(self, exception_type, exception_value, traceback)`: performs cleanup. if it returns false any exceptions passed to it are thrown. If it returns True, then exceptions are suppressed.

## TBD
we can use @contextmanager for this as well. Will
