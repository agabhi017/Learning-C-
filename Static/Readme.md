# Static in C++

The keyword static can be used in 3 different settings in C++ - inside of a class/struct definition (with methods/variables), outside of it (for a variable or a method) 
or inside a method (local static)

### Static keyword outside a class defintion:
* The keyword static can be used for a variable or a method to make that variable/method private to that particular transalation unit (`.cpp` file)
* In other words the scope of a static variable/method is restricted/local to a particular transaltion unit.
* In this case the linker will not look to link the static variables/methods at the linking stage
* This should be used if the variables/functions are not required/desired to be used outside of a `.cpp` file
* The `extern` symbol is used in cases when we want the linker to look for the name resoultion in an external (or different) translation unit. In such cases if the variable is 
declared as static in the external `cpp` file, the compiler will throw a linker error.
* In simpler words, marking a variable/method `static` is same as declaring it private (to an `obj` or a `cpp` file).
* It should be used when we are definite that the global variables/functions should be private/restricted to only some parts of the implementation and not to be used everywhere. It is recommended to use static keyword always with such kinds of functions/variables.


### Local Static



### Static inside a class/struct definition

* Static variables.membert functions are accessed by using the class name/scope and not through an object/class instantiation.

#### Static Variables
* Static variables inside a class/struct share a common memory across all the instances of that class.
* Static variables are somewhat global variables inside a namespace and that namespace is the class.
* For instance, if we would like to count the number of objects of a particular class, we can declare a static count variable and increment it in the constructor every time 
the class is instantiated. In this way there will only be a single count variables across all the objects of that class and to access it we do not need an object to be able to access it.
* These static variables need to be defined outside the class definition using the class's name resoultion. For example `myClass::static_variable_1`.
* These can be both public as well as private. If they are public, they can be accessed directly using the namespace and inorder to access private static variables, we need 
static member functions.

#### Static methods/functions
* Since private static variables cannot be accessed directly, static methods are required to access them.
* Just like static variables, these methods are independent of the class instance and `they do not have access to a class instance`. That is, they do not have access to the 
`this` pointer.
* Static methods can only access static variables and do not have access to other non-static variables of the class.
* Just like static variables, they are accessed using the namespace resolution of the class. We may choose to define static methods either inside or outside a class.
