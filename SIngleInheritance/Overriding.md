# Overriding Functionality
### When we inherit from another class, we inherit its attributes, including all callables
* -> we can choose to redefine an existing callable in the sub class
     * -> this is called overriding
```python
class Person:
  def say_hello(self):
    return 'Hello!'
  def say_bye(self):
    return 'Bye!'
    
class Student(Person):
  def say_hello(self):
    return 'Yo!'
    
p = Person() 
p.say_hello() -> Hello!
p.say_bye() -> Bye!
  
s = Student()
s.say_hello() ->  Yo!
s.say_bye()  -> Bye!
```

### When we create any class, we can override any method defined in the parent class, including
* -> inherited ones
* -> those defined in object

```python
class Person:
  def __init__(self, name): #overrides __init__ in object
    self.name = name
  def __repr__(self): #overrides __repr__ in object
    return f'Person(name={self.name})'
    
class Student(Person):
  def __repr__(self): #overrides __repr__ in Person, inherits __init__ from Person
    return f'Student(name={self.name})'
    
p = Person('john') str(p) -> Person(name=john)
s = Student('eric'') str(s) -> Student(name=eric)
```

## Tip
Objects have a property: ```__class__``` -> returns the class the object was created from</br>

Classes have a property: ```__name__```  -> returns a string containing the name of the class<br/>

To get the name (string) of the class used to create an object -> ```object.__class__.__name__```<br/>


### We can do this to implement what was done above:
```python
class Person:
  def __init__(self, name):
    self.name = name
  def __repr__(self):
    return f'{self.__class__.__name__}(name={self.name})'

class Student(Person):
  pass
```


Suppose we have this type of hierarchy:
Person
- eat()   -> "Person eats"<br/>
- sleep() -> "Person sleeps"<br/>
- work()  -> "Person works"<br/>
- routine() -> eat() work() sleep()<br/>
p = Person()
p.routine() -> Person eats Person works Person sleeps

Now we create a Student class that overrides the work() method only:<br/>
Student:
- work() -> "Student studies" 

### what happens when we call routine() on a Student instance?
s = Student() -> s.routine()
* -> runs routine as defined in Person class – but bound to s
* -> routine calls 
* -> eat() in Person class bound to s
* -> sleep() in Person class bound to s
* -> calls work() -> finds the override in Student!!!
    * -> uses the override in Student<br/>
Output :<br/>
* -> Person eats
* -> Student studies
* -> Person sleeps
