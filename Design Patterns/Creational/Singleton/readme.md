# Singleton Design Pattern
* This pattern restricts the instantiation of a class to one object.
* It is a type of creational pattern and involves only one class to create methods and specified objects.
* It provides a global point of access to the instance created.
<p align="center"><img src="https://i.imgur.com/KCG3Iz7.png" alt="Singleton Design Pattern"></p>

```python
# singleton.py

class Singleton:
   __instance = None
   @staticmethod 
   def getInstance():
      """ Static access method. """
      if Singleton.__instance == None:
         Singleton()
      return Singleton.__instance
   def __init__(self):
      """ Virtually private constructor. """
      if Singleton.__instance != None:
         raise Exception("This class is a singleton!")
      else:
         Singleton.__instance = self
s = Singleton()
print s

s = Singleton.getInstance()
print s

s = Singleton.getInstance()
print s
```

```python
# singleton_decorator.py

def singleton(class_):
    instances = {}
    def getinstance(*args, **kwargs):
        if class_ not in instances:
            instances[class_] = class_(*args, **kwargs)
        return instances[class_]
    return getinstance

@singleton
class MyClass(BaseClass):
    pass
```