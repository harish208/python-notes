## Dunder methods

  Python syntax is a wrapper over dunder methods (double underscore `__method__` methods). 
  
  Presence of some dunder methods with special names in class signifies specific capabilites to the python runtime

| Syntax | Python calls | Purpose |
|---|---|---|
| `len(obj)` | `obj.__len__` | size |
| `a + b` | `a.__add__` (then `b.__radd__`) | addition |
| `a / b` | `a.__truediv__` (then `b.__rtruediv__`) | division |
| `a / b` (pathlib) | `a.__truediv__` | path join |
| `with obj as x` | `obj.__enter__` / `obj.__exit__` | setup/cleanup |
| `bool(obj)` | `obj.__bool__`, fallback `__len__` | truthiness |
| `repr(obj)` | `obj.__repr__` | debug representation |

## Dunder methods are always looked up on the class type. Not on the object itself

```python
class Dog:
  def __len__(self):
    return 42

print(len(Dog())) # Prints 42
```


