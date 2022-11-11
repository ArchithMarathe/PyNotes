## Data Attributes, Classes and Instances
  Let's focus on data attributes first (i.e. not functions) 
  ```
  class MyClass:
    language = 'Python'
  my_obj = MyClass()
  MyClass.__dict__ -> {'language': 'Python'}
  my_obj.__dict__ -> {}
  ```
  MyClass.language -> Python starts looking for language attribute in MyClass namespace<br/>
  MyClass.language -> 'Python'
  
  my_obj.language -> Python starts looking in my_obj namespace
  * -> if it finds it, returns it
  * -> if not, it looks in the type (class) of my_obj, i.e. MyClass
  * -> 'Python'

``` python
class MyClass:
  language = 'Python'

my_obj = MyClass() 
MyClass.language -> 'Python'

my_obj.__dict__ -> {}
my_obj.language = 'java'
my_obj.__dict__ -> {'language': 'java'} #instance attribute
my_obj.language -> 'java'

MyClass.language -> 'Python'
other_obj = MyClass()
other_obj.__dict__ = {}
other_obj.language -> 'Python'

class MyClass:
  language = 'Python' #class attribute
```
