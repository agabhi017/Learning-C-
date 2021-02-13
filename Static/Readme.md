# Static in C++

The keyword static can be used in 3 different settings in C++ - inside of a class definition (with methods/variables), outside of it (for a variable or a method) 
or inside a method (local static)

### Static keyword outside a class defintion:
* The keyword static can be used for a variable or a method to make that variable/method private to that particular transalation unit (`.cpp` file)
* In this case the linker will not look to link the static variables/methods at the linking stage
* This should be used if the variables/functions are not required/desired to be used outside of a `.cpp` file

### Local Static



### Static inside a class definition

