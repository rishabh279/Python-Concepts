* First Class Function 
  
  * A programming language is said to have first-class functions if it treats functions as first-class citizens.

* First Class Citizen
  
  * In [programming language design](https://en.wikipedia.org/wiki/Programming_language#Design_and_implementation "Programming language"), a **first-class citizen** (also **type**, **object**, **entity**, or **value**) in a given [programming language](https://en.wikipedia.org/wiki/Programming_language "Programming language") is an entity which supports all the operations generally available to other entities. These operations typically include being passed as an argument, returned from a function, modified, and assigned to a variable.

* Following snippets illustrates first class function concept according to definition:
  
  * Assigned to a variable
    
    ```python
    def square(x):
        return x*x
    f = square
    print(square)
    print(f(5))      
    ```
  
  * Passed as argument    
    
    ```python
    def cube(x):
        return x*x*x
    
    def custom_map(func, arg_list):
        result = []
        for i in arg_list:
            result.append(func(i))
        return result
    cubes = custom_map(cube, [1, 2, 3, 4, 5])
    print(cubes)
    ```
  
  * Passed as function
    
    ```python
    def logger(msg):
        def log_message():
            print('Log:', msg)
        return log_message
    
    log_hi = logger('log msg')
    log_hi()
    ```
