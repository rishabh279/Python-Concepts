## Oops - Classes and Attributes

* **Example-1**
  
  ```python
  class Employee:
  
      def __init__(self, first, last, pay):
          self.first = first
          self.last = last
          self.email = first + '.' + last + '@email.com'
          self.pay = pay
  
      def fullname(self):
          return '{} {}'.format(self.first, self.last)
  
  emp_1 = Employee('Corey', 'Schafer', 50000)
  emp_2 = Employee('Test', 'Employee', 60000)
  # Here emp_1.fullname() == Employee.fullname(emp_1)
  emp_1.fullname()
  Employee.fullname(emp_1)
  ```

* **Example-2**[Classes and Instance Variables]
  
  ```python
  class Employee:
  
      num_of_emps = 0
      raise_amt = 1.04
  
      def __init__(self, first, last, pay):
          self.first = first
          self.last = last
          self.email = first + '.' + last + '@email.com'
          self.pay = pay
  
          Employee.num_of_emps += 1
  
      def fullname(self):
          return '{} {}'.format(self.first, self.last)
  
      def apply_raise(self):
          self.pay = int(self.pay * self.raise_amt)
  
  #Update instance creation count globally
  print(Employee.num_of_emps)
  emp_1 = Employee('Corey', 'Schafer', 50000)
  emp_2 = Employee('Test', 'Employee', 60000)
  print(Employee.num_of_emps)
  
  Employee.apply_raise(emp_1)
  
  print(Employee.raise_amt)
  print(emp_1.raise_amt)
  print(emp_2.raise_amt)
  ```
