#Classes vs Structs

### Classes
* Classes allow us to create custom data types by grouping variables/attributes and then adding functionalities(functions/methods) on top of them.
* Classes do not actually help us achieve something which cannot be written otherwise. They are a functionality to make our code more organized syntactically and easy to follow.
* By default the `visibility` of the variables and the methods inside the classes is private.

### Structures or Structs
* Structs are same as clasess with just one difference - the defualt `visibility`.
* BY defualt, the members of a struct are `public` as compared to a class where they are `private`. And thats all!
* The actual difference might lie in the usage which inturn depends on the coding style. 
* For example one mayh prefer to use structs to hold data and use classes to handle more complex information and functionality and even concepts like inheritance.
* For instance, if a struct is inherited from a class, some compilers may give a warning.
* A reason why they exist is because of the C compatibility. Since C does not have the concept of classes but they do have structures, `structs` exists in C++ so that the code
can be compatible with C compilers.
