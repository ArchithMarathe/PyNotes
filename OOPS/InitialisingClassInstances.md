## Initializing Class Instances
  When we instantiate a class, by default Python does two separate things:<br/>
  * ->creates a new instance of the class
  * ->initializes the namespace of the class
```python
class MyClass:
  language = 'Python' 
obj = MyClass() 
obj.__dict__ -> {}
```
We can provide a custom initializer method that Python will use instead of its own:
```python
class MyClass:
  language = 'Python'
  def __init__(obj, version): #notice that __init__ is defined to work as a bound instance method
    obj.version = version
 ```
 Deconstructing this…
```python
class MyClass:
  language = 'Python'
  def __init__(obj, version): #self (convention)
    obj.version = version
```
language is a class attribute -> in class namespace<br/>
```__init__``` is a class attribute -> in class namespace (as a function)

when we call MyClass('3.7')<br/>

* -> Python creates a new instance of the object with an empty namespace
  * -> if we have defined an ``` __init__ ``` function in the class
      * -> it calls ``` obj.__init__('3.7) ``` -> bound method -> ``` MyClass.__init__(obj, '3.7') ```
      * -> our function runs and adds version to obj's namespace
      * -> version is an instance attribute
      * -> ``` obj.__dict__ ``` -> {'version': '3.7'}

a standard convention is to use an argument named self


## Important!
By the time ```__init__``` is called
Python has already created the object and a namespace for it (like a ```__dict__``` in most cases) <br/>
then ```__init__``` is called as a method bound to the newly created instance

We can actually also specify a custom function to create the object<br/>
```__new__```<br/>
we'll come back to this later <br/>

But ```__init__``` is not creating the object, it is only running some code after the instance has been created.
