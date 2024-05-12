# Abstract Factory

The abstract factory 'provides an interface for creating families of related or dependent orbjects without specifying their concrete classes'.

The basic use of this is by creating an abstract 'parent' class which is never instantiated but instead exists only to define the INTERFACE for concrete, child classes.

For example, let's say we have a program that re-organizes your files on your computer!
However, we know that MacOS and Windows systems have different ways of working with files - they have different default directories (`C:` vs `~`), different directory structures, and also use different notations for file paths!
How can we make a program which runs *regardless of what OS it's running on?*

Using an Abstract Factory design, we can generate different versions of the application to run depending on an input that can be determined at runtime. For example, we can create an Abstract Factory `AppGenerator` which does two things:
- Determines the client's OS
- Creates either a `MacApp` or a `WindowsApp` object to return to the rest of the application to use in running everything.

The key of the Abstract Factory is that **every possible object returned by the factory has the exact same interface.** So, the app can work exactly the same regardless of the operating system, because all OS-specific low-level details are encapsulated in the App that the factory returns - and each one has the same interface.
Therefore, the rest of the program can call all of the expected methods of the returned App and not care at all how they're implemented!

Another way to say this is that the abstract factory is a singleton - there is never more than 1 - and it produces an 'abstract product' which has a fixed interface. The exact instantiation of this product is done behind the scenes: The abstract factory determines which concrete factory to call - the concrete factory returns a concrete product which the abstract factory then forwards to the client. The client knows how to use the concrete product because the abstract factory already advertised the abstract product which has the same interface.