## Property Decorators

* The idea behind the property and setter decorators is to get the functionality of getter and setter as seen in other oops languages like Java. In the below example if we have to change the first name, then it will not reflect globally in code, eg:

* **Example-1**
  
  ```python
  class Employee:
  
      def __init__(self, first, last):
          self.first = first
          self.last = last
          self.email = first + last + '@email.com'
  
      def get_email(self):
          return self.first + self.last + '@email.com'
  emp_1 = Employee('John', 'Smith')
  emp_1.first = 'Tom'
  print(emp_1.first)
  print(emp_1.get_email())
  ```

* If we see the output, we can see that the change in firstname is not reflected in email, to do so we have to do the following change.

* **Example-2**
  
  ```python
  class Employee:
  
      def __init__(self, first, last):
          self.first = first
          self.last = last
          self.email = first + last + '@email.com'
  
      def get_email(self):
          return self.first + self.last + '@email.com'
  
  
  emp_1 = Employee('John', 'Smith')
  emp_1.first = 'Tom'
  print(emp_1.first)
  print(emp_1.get_email())
  ```

* But the problem with above is that we need to make change in code that is displayed to user ie. email(). To treat get_email as property we use 

* **Example-3**
  
  ```python
  class Employee:
  
      def __init__(self, first, last):
          self.first = first
          self.last = last
          self.email = first + last + '@email.com'
  
      def fullname(self):
          return '{} {}'.format(self.first, self.last)
  
      @property
      def get_email(self):
          return self.first + self.last + '@email.com'
  emp_1 = Employee('John', 'Smith')
  emp_1.first = 'Tom'
  print(emp_1.first)
  print(emp_1.get_email)
  ```

* Now in the above example, in case we need to change the fullname, there is no option. We can do this by setting fullname as setter method as shown below:

* **Example-4**
  
  ```python
  class Employee:
  
      def __init__(self, first, last):
          self.first = first
          self.last = last
  
      @property
      def email(self):
          return '{}.{}@email.com'.format(self.first, self.last)
  
      @property
      def fullname(self):
          return '{} {}'.format(self.first, self.last)
  
      @fullname.setter
      def fullname(self, name):
          first, last = name.split(' ')
          self.first = first
          self.last = last
  emp_1 = Employee('John', 'Smith')
  emp_1.fullname = "Corey Schafer"
  
  print(emp_1.first)
  print(emp_1.email)
  print(emp_1.fullname)
  ```

* Similarly if we have to delete employee full name we can do this we deleter method.

* **Example-5**
  
  ```python
  class Employee:
  
      def __init__(self, first, last):
          self.first = first
          self.last = last
  
      @property
      def email(self):
          return '{}.{}@email.com'.format(self.first, self.last)
  
      @property
      def fullname(self):
          return '{} {}'.format(self.first, self.last)
  
      @fullname.setter
      def fullname(self, name):
          first, last = name.split(' ')
          self.first = first
          self.last = last
  
      @fullname.deleter
      def fullname(self):
          print('Delete Name!')
          self.first = None
          self.last = None
  
  emp_1 = Employee('John', 'Smith')
  emp_1.fullname = "Corey Schafer"
  
  print(emp_1.first)
  print(emp_1.email)
  print(emp_1.fullname)
  
  del emp_1.fullname
  ```
  
  
