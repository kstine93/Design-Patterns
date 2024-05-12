# Builder

The builder pattern 'separates the construction of a complex object from its representation, so that the same construction process can create different representations'.
A non-code example would be building a house - we can define different modules (or objects) that know how to create walls, windows, doors, etc. and then building a house is as simple as combining those high-level objects in the right way.

Let's take as an example a parsing program for social media posts. The program needs to be able to take a large variety of media in different languages and produce English textual versions of all of them.
We can tackle this problem with a builder program:
- We can first make a primary 'MediaConverter' class to coordinate everything.
- Then, we can create a 'FormatConverter' class to convert all media into text format. This might also need to have subclasses to handle videos, audio, and probably subclasses of those to handle different languages in each of those media types.
- Then, we can create a 'LanguageTranslator' class to convert all text-based content into English.

This format lets us take a big problem and break it down into smaller problems that are more atomic. We then group those problems and keep them within a dedicated scope to make maintaining them easier (e.g., the code for converting videos to text would have subclasses for Polish, Danish, Spanish, etc.; in a separate module, we would have the code for converting emojis to text - since this is a completely different operation).

Another aspect of the Builder pattern is that it's meant to be easy to switch out pieces relatively easily. So, if we wanted to translate everything into SPANISH instead of English, we could switch out our 'LanguageTranslator' class to do that, but leave the 'FormatConverter' class untouched. Since the primary (a.k.a. "director") class is the only one that knows about all of the components, we only have to make a change there.
