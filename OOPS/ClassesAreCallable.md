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
