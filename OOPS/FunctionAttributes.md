## Methods
  Method is an actual object type in Python
    like a function, it is callable
    but unlike a function it is bound to some object
    and that object is passed to the method as its first parameter

  ```my_obj.say_hello()``` -> say_hello is a method object
 * ->it is bound to my_obj
 * ->when my_obj.say_hello is called, the bound object my_obj is injected as the first parameter to the method say_hello
 so it's essentially calling this: 
    ```MyClass.say_hello(my_obj)```

One advantage of this is that say_hello now has a handle to the object's namespace! -> the object it is bound to <br/>
But there's more to it than just calling the function this way – method object
### Methods are objects that combine:
  -> instance (of some class)
  -> function
 like any object it has attributes
  ```__self__``` -> the instance the method is bound to
  ```__func__``` -> the original function (defined in the class)

```calling obj.method(args)``` -> ```method.__func__(method.__self__, args)```

 ```python
 class Person:
 #p.hello.__func__ is hello
    def hello(self):
        pass
        
   #p.hello.__self__ is p
    p = Person()
   
```
## Instance Methods
  This means we have to account for that "extra" argument when we define functions in our classes – otherwise we cannot use them as methods bound to our instances.

  These functions are usually called instance methods
```python
class MyClass:
  def say_hello(obj): #first param will receive instance object, we often call this an instance method but not actually a method object yet!
      print('Hello World!') #at this point it's just a regular function
```
  
```python
  my_obj = MyClass()
  my_obj.say_hello #now it's a method and is bound to my_obj, an instance of MyClass instance method.
```
 

```python
my_obj.say_hello() -> 'Hello World!'
-> MyClass.say_hello(my_obj)
```
Of course functions in our classes can have their own parameters
When we call the corresponding instance method with arguments -> passed to the method as well
```python
class MyClass:
  language = 'Python'
  def say_hello(obj, name):
    return f'Hello {name}! I am {obj.language}. '
```
And the method still receives the instance object reference as the first argument, we have access to the instance (and class) attributes!
```python
python = MyClass()
python.say_hello('John') -> MyClass.say_hello(python, 'John')
-> 'Hello John! I am Python'

java = MyClass()
java.language = 'Java'
java.say_hello('John') -> MyClass.say_hello(java, 'John')
-> 'Hello John! I am Java'
```
