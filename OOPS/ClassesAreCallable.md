## Classes are Callable
  When we create a class using the class keyword Python automatically adds behaviors to the class in particular:
  * -> it adds something to make the class callable
  * -> the return value of that callable is an object
  * -> the type of that object is the class object
  
we say the object is an instance of the class
```
my_obj = MyClass()
type(my_obj) -> MyClass
isinstance(my_obj, MyClass) -> True
```
also called class instantiation
or instantiating the class

## Instantiating Classes
  When we call a class, a class instance object is created
  This class instance object has its own namespace
  * -> distinct from the namespace of the class that was used to create the object
  
  This object has some attributes Python automatically implements for us:
  * -> ```__class__``` tells us which class was used to instantiate the object
  * -> ```__dict__``` is the object's local namespace
  
  prefer using ``` type(obj) ``` instead of ``` obj.__class__ ```
