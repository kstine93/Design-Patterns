# Factory Method

The factory method is for 'creating an interface to create an object, but letting SUBCLASSES decide which class to instantiate'.

So, we would really have here a callable method that returns a generic interface. Then, the method decides to instantiate a particular subclass given some input.

It appears that the factory method is kind of a smaller version than abstract factory. Whereas the abstract factory is meant to handle the creation of multiple components, the factory method is just for creating 1. So the use case might be for when we have most of the application be exactly the same, except for one point of deviation.

For example, let's say that we're writing a program that estimates delivery times for Amazon. The delivery calculation is basically the same except for what method of transportation is used: plane, sea or truck. We create a factory method to generate an object representing one of these transport methods and then use that object to calculate the data we need for the ETA.
