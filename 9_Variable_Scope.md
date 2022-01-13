## Variable Scope

* The variable scope in python follows the LEGB rule ie. Local, Enclosing, Global, Built-in.

* Here in the below example variables gets print in console according to the scope in which they are defined. This also gives error at printing y which is outside the scope of the y variable.

* ```python
  x = 'x_global'
  def test():
      y = 'y_local'
      print(y)
  test()
  print(x)
  print(y)
  ```

* Another example:

* ```python
  def test(x):
      x = 'x_local'
      print(x)
  x = 'test'
  test(x)
  print(x)
  ```

* In order to change the global variable in local context we do so by defining the global variable.

* ```python
  x = 'x_global'
  def test():
      global x
      x = 'x_local'
      print(x)
  test()
  print(x)
  ```

* According to the LEGB rule, second is enclosing which means that inner funcs have access to variables that are defined in local context of their outer functions:

* ```python
  def outer():
      x = 'outer_x'
  
      def inner():
          x = 'inner_x'
          print(x)
  
      inner()
      print(x)
  outer()
  ```

* ```python
  def outer():
      x = 'outer_x'
  
      def inner():
          #x = 'inner_x'
          print(x)
  
      inner()
      print(x)
  outer()
  ```

* If we have to change the variable define in outer function by inner function we can do with either global or nonlocal

* ```python
  def outer():
      x = 'outer_x'
  
      def inner():
          nonlocal x
          x = 'inner_x'
          print(x)
  
      inner()
      print(x)
  outer()
  ```

* At last, python check the builtins which can shown by:

* ```python
  import builtins
  print(dir(builtins))
  m = min([5, 4, 3, 2, 1])
  print(m)
  ```




