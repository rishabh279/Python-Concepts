## Decorators

* First class functions allow us to treate functions like any other object for eg we can pass funcs as arguments to another funcs, we return fucns and we can assign funcs to variable. See individual topic for more detail.

* Closure allow us to take the advantage first class functions and return inner function that remembers and have access to variables local to scope in which they were created. See individual topic for more detail.

* Decorator is a function that takes another func as an argument, adds some kind of functionality and returns another func, doing all this without altering the source code of the original function that we passed in.

* **Example-1**
  
  ```python
  def decorator_function(original_function):
     def wrapper_function():
         print(f'Wrapper func executed before {original_function.__name__}')
         return original_function()
     return wrapper_function
  
  def display():
     print('Display func ran')
  
  decorated_display = decorator_function(display)
  decorated_display()
  ```

* **Example-2**
  
  ```python
  def decorator_function(original_function):
      def wrapper_function():
          print(f'Wrapper func executed before {original_function.__name__}')
          return original_function()
      return wrapper_function
  
  @decorator_function
  def display():
      print('Display func ran')
  
  display()
  ```

* **Example-3**
  
  ```python
  def decorator_function(original_function):
      def wrapper_function(*args, **kwargs):
          print(f'Wrapper func executed before {original_function.__name__}')
          return original_function(*args, **kwargs)
      return wrapper_function
  
  @decorator_function
  def display():
      print('Display func ran')
  
  @decorator_function
  def display_info(name, age):
      print(f'Name is {name} and age is {age}')
  
  display_info('Tommy', 22)
  ```

* **Example-4**
  
  ```python
  # Decorators
  from functools import wraps
  import logging
  import time 
  
  def my_logger(orig_func):
      logging.basicConfig(filename='{}.log'.format(orig_func.__name__), level=logging.INFO)
      @wraps(orig_func)
      def wrapper(*args, **kwargs):
          logging.info(
              'Ran with args: {}, and kwargs: {}'.format(args, kwargs))
          return orig_func(*args, **kwargs)
  
      return wrapper
  
  def my_timer(orig_func):
      @wraps(orig_func)
      def wrapper(*args, **kwargs):
          t1 = time.time()
          result = orig_func(*args, **kwargs)
          t2 = time.time() - t1
          print('{} ran in: {} sec'.format(orig_func.__name__, t2))
          return result
  
      return wrapper
  
  @my_logger
  @my_timer
  def display_info(name, age):
      time.sleep(1)
      print('display_info ran with arguments ({}, {})'.format(name, age))
  
  display_info('Tom', 22)
  ```
