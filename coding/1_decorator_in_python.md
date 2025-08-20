# Python Decorators

A decorator is a function that takes another function and returns a new one with modified or extended behavior.

It’s like a **wrapper** around your function. You don’t change the original function itself, you just add some extra capabilities to it.

## Why use them?

- 📊 **Logging** – e.g., print the function call time or its arguments.  
- ⏱ **Measuring execution time** – see how long a function takes to run.  
- 🔒 **Access control** – e.g., in web applications.  
- ♻️ **Caching results** – e.g., using `functools.lru_cache`.  
- 🧹 **Avoid code duplication** – “wrap it once” and the function gains extra powers.

# Example
```python
import time

# decorator
def timer(func):
    def wrapper(*args, **kwargs):
        start = time.time()
        result = func(*args, **kwargs)  # call the original function
        end = time.time()
        print(f"Function {func.__name__} took {end - start:.4f} seconds")
        return result
    return wrapper

# use the decorator 
@timer
def slow_function():
    time.sleep(2)
    return "done"

print(slow_function())
```