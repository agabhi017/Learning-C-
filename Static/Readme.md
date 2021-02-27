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
* 

