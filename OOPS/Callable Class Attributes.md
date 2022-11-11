Attribute values can be :
  1. Any object  
  2. Other classes 
  3. Any callable or anything…

class MyClass:
  language = 'Python'
  def say_hello():
    print('Hello World!')

say_hello is also an attribute of the class -> it's value happens to be a callable


MyClass.__dict__ -> mappingproxy({'language': 'Python','say_hello': <function __main__.MyClass.say_hello()>, ...})

How do we call it?

We could get it straight from the namespace dictionary:
1. my_func = MyClass.__dict__['say_hello']
   my_func() -> 'Hello World!'
2. MyClass.__dict__['say_hello']() -> 'Hello World!'

or we could use getattr:
getattr(MyClass, 'say_hello')() -> 'Hello World!'

or we can use dot notation:
MyClass.say_hello() -> 'Hello World!'
