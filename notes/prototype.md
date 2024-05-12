# Prototype

The prototype is a template for creating copies. Let's imagine that we have a particular object that's instantiated by the client. The client provides lots of input data and we get the result. Now, we want to create copies of this object to do different things with (e.g., convert into various formats). The issue is that **it's not always possible to copy something from the outside**.
We don't necessarily know how the object from the client was created and if we try to re-instantiate it ourselves, then we'll need to be tightly coupled to the object type- which is not ideal.

The solution is a prototype pattern: before the client ever creates their custom object, we install a `.copy()` method into the base object that has all of the information needed to make a complete copy of the object.

Now, our downstream code can just call this .copy() method on the original object **and not care at all about the innards of the object**. So, even though this in-depth copy operation is happening long after anyone is modifying the object, the code that calls it doesn't need any special information to do it!