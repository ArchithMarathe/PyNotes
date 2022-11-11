## Defining Class Attributes in Python
  ``` class MyClass:
        language = 'Python'
        version = '3.6' ```
    
  version and language are attributes of class MyClass
  
 Retrieving Attribute Values from Objects
 
  1. getattr function  -> Syntax : getattr(object_symbol, attribute_name, optional_default)
     Eg : getattr(MyClass, 'language') -> 'Python'
          getattr(MyClass, 'x') -> AttributeError exception (Exception if attribute doesnt exist)
          getattr(MyClass, 'x', 'N/A') -> 'N/A' (Returns default value if attribute doesnt exist)
          
  2. dot notation (shorthand)
     MyClass.language -> 'Python'
     MyClass.x -> AttributeError exception  (Exception if attribute doesnt exist)
  
  
  Setting Attribute Values in Objects
    
    1. setattr function -> Syntax : setattr(object_symbol, attribute_name, attribute_value)
       Eg : setattr(MyClass, 'version', '3.7')
    
    2. dot notation
       Eg : MyClass.version = '3.7'
    
    Python is a dynamic language i.e it creates the attributes at runtime if they dont exist while using setattr.
    
    
   Where is the Class State stored?
    In a dictionary
    A class has a __dict__ attribute that returns a mappingproxy object which is a read-only dictionary of class attributes.
    __dict__ not directly mutable, can be muted with setattr.
    Ensures keys of the dict are strings to speed up things for python (can use id() on strings rather than == (__eq__), which is slower)
    
    
    Deleting Attributes
    
    We can remove the Class attributes at runtime:
    
    1. delattr(obj_symbol, attribute_name)   -> Gives AttributeError if attribute doesnt exist
    2. del keyword                           -> Gives AttributeError if attribute doesnt exist
    Eg : delattr(MyClass, 'version') or del MyClass.version
    
    Accessing the Namespace Directly
    
    The __dict__ attribute of a class returns a mappingproxy object.
    Although this is not a dict, it is still a hash map (dictionary), so we can at least read access the
    class namespace directly – not common practice!!
    
    1. MyClass.language
    2. getattr(MyClass, 'language')
    3. MyClass.__dict__['language']
    
    Be careful with this – sometimes classes have attributes that don't show up in that dictionary! 
      Eg : __name__ of a class doesnt exist in the __dict__
   
   
