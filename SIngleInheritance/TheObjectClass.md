# The object Class
When we define a class that does not inherit from another class explicitly
* -> Python makes the class inherit from object implicitly
* -> object is a class (even though it does not use a camel case)<br/><br/>
```type(object) -> type```<br/>
```type(Person) -> type```

```python
class Person:
      pass 
```
same as
```python
class Person(object):
  pass
```
->this means every class we create is a subclass of object

``` issubclass(Student, object) -> True ```<br/>
``` isinstance(s1, object) -> True ```

## Implications of inheriting from object
* -> any class we create automatically inherits behaviors and attributes from the object class :
```python
* -> __name__
* -> __init__
* -> __repr__
* -> __hash__
* -> __new__
* -> __eq__
```
and many more…
### So even if we create an "empty" class: 
```python
class Person:
  pass
p = Person()
p.__repr__ -> <__main__.Person object at 0x106cb79e8>
p.__hash__  -> -9223372036579215458
p == p -> True
```
it will use whatever default implementation object has defined
