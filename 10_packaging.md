## Packaging

* When a `.py` file is imported as a module, Python sets the special **dunder** variable [`__name__`](https://realpython.com/python-main-function/) to the name of the module. However, if a file is run as a standalone script, `__name__` is (creatively) set to the string `'__main__'`. Using this fact, you can discern which is the case at run-time and alter behavior accordingly


