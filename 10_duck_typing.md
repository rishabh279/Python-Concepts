## Duck Typing

* In this concept if an object walks like a duck and quacks like a duck which means simply that we dont care about what type of object we are work with. We only care about what we ask the object to do.

* ### Example
  
  ```python
  class Duck:
  
      def quack(self):
          print('Quack, quack')
  
      def fly(self):
          print('Flap, Flap!')
  
  
  class Person:
  
      def quack(self):
          print("I'm Quacking Like a Duck!")
  
      def fly(self):
          print("I'm Flapping my Arms!")
  
  
  ```

* ### Not Duck Typed
  
  ```python
  def quack_and_fly(thing):
      #Not Duck-Typed (Non-Pythonic)
      if isinstance(thing, Duck):
          thing.quack()
          thing.fly()
      else:
          print('This has to be a Duck!')
  
  
  d = Duck()
  quack_and_fly(d)
  
  p = Person()
  quack_and_fly(p)
  
  ```

* ### Duck Typed
  
  ```python
  #Duck-Typed
  def quack_and_fly(thing):
      thing.quack()
      thing.fly()
  
  d = Duck()
  quack_and_fly(d)
  
  p = Person()
  quack_and_fly(p)
  
  ```

 

## Easier To Ask Forgiveness Than Permission(EAFP)

* In the below example we are asking permmission for each thing:
  
  ```python
  def quack_and_fly(thing):
      
      if hasattr(thing, 'quack'):
          if callable(thing.quack):
              thing.quack()
  
      if hasattr(thing, 'fly'):
          if callable(thing.fly):
              thing.fly()
  ```

* In the below example it shows that by saying lets try to achieve what we want to achieve, we will handle it(forgiveness) if something happens
  
  ```python
  def quack_and_fly(thing):
          try:
              thing.quack()
              thing.fly()
              thing.bark()
          except AttributeError as e:
              print(e)
  ```

* Another example without EAFP
  
  ```python
  person = {'name': 'Jess', 'age': 23, 'job': 'Programmer'}
  person = {'name': 'Jess', 'age': 23}
  
  
  if 'name' in person and 'age' in person and 'job' in person:
      print(f"I'm {name}. I'm {age} years and I am a {job}."
  else:
      print('Some key are missing')
  ```

* With EAFP
  
  ```python
  try:
      print(f"I'm {name}. I'm {age} years and I am a {job}."
  except KeyError as e:
      print("Missing {} key".format(e))
      
  ```

* Another Example without EAFP
  
  ```python
  person = {'name': 'Jess', 'age': 23, 'job': 'Programmer'}
  person = {'name': 'Jess', 'age': 23}
  
  
  if 'name' in person and 'age' in person and 'job' in person:
      print(f"I'm {person['name']}. I'm {person['age']} years and I am a {person['job']}.")
  else:
      print('Some key are missing')
  ```

* With EAFP
  
  ```python
  try:
      print(f"I'm {person['name']}. I'm {person['age']} years and I am a {person['job']}.")
  except KeyError as e:
      print(f"Missing {e} key")
  
  ```

* Without EAFP
  
  ```python
  my_list = [1, 2, 3, 4]
  if len(my_list) >= 4:
      print(my_list[3])
  else:
      print('Index does not exist')
  ```

* With EAFP
  
  ```python
  try:
      print(my_list[5])
  except IndexError as e:
      print(e)
  ```

* Wy it is convinent to easy to ask forgiveness than permission?
  
  * It is faster.
  
  * It is more readable. Although it is debatable.

* Why faster example helps to avoid race condition->
  
  ```python
  import os 
  #with race condition
  my_file = '/tmp/test.txt'
  
  if os.access(my_file, os.R_OK):
      with open(my_file) as f:
          print(f.read())
  else:
      print('File can not be accessed')
  
  ```
  
  ```python
  #without race condition 
  try:
      f = open(my_file)
  except IOError as e:
      print('File can not be accessed')
  else:
      with f:
          print(f.read())
  ```

* In above example in first case,  even if we dont have access we will try to open the file while this is not the case  of second example.
