# Factory Design Pattern
* The factory pattern comes under the creational patterns list category.
* It provides one of the best ways to create an object.
* In factory pattern, objects are created without exposing the logic to client and referring to the newly created object using a common interface.
* Factory patterns are implemented in Python using factory method.
    * When a user calls a method such that we pass in a string and the return value as a new object is implemented through factory method.
    * The type of object used in factory method is determined by string (or identifier) which is passed through method.

<img src="https://i.imgur.com/LiCg2Xd.jpg" alt="Factory Design Pattern" align="center">

* To get the objects class, we can either use `__subclasses__()` or `globals()[className]`

