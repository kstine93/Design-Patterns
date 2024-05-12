# Singleton

A singleton is a special object that should only ever have one instance.
In this way, the singleton is more about encapsulating behavior in your program that should only be done in one place or by one actor (e.g., to prevent race conditions). The singleton is less about representing objects which - by definition - can have multiple instances.

For example, we may have a 'DatabaseAccess' class which encapsulates the logic necessary to connect and query the database.
We don't ever need to have multiple instances of this class - because each instance would do the same thing. Using this singleton class is just a way to keep all of our database stuff together and easily pass this object around the program for various functions to use when they want to access the database.

Note that in Python modules basically act as singletons- they are 'imported' and then re-used throughout the application without copying. So, there's very rarely a need to instantiate singletons in Python - rather, you should probably just put the code for them into a module that you can import.
However, it is still possible to create a singleton class in Python - the only requirement is limiting instantiation:
```python
class SingletonClass(object):
  def __new__(cls):
    if not hasattr(cls, 'instance'):
      cls.instance = super(SingletonClass, cls).__new__(cls)
    return cls.instance
```

**Side Note:**
The singleton can be overused and has some disadvantages:
- Multithreaded environments pose problems for the singleton, since they can sometimes accidentally create multiple copies of it (this also applies if we have replicas of a singleton microservice, for example).
- The singleton can mask bad design - such as when components within the singleton know too much about each other.