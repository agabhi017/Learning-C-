# Linking and compilation in C++

* Compilation happens in 2 stages in C++ - source code compilation(translation) and linking (of object files)
* Each source code or `.cpp` file is called as a translation unit and will generate an object file upon compilation

### Compilation
* Compilation is simply the process of transalting the text in the `.cpp` file into machine code - the one which can be executed.
* At the compilation stage, the compiler can throw syntax errors, or missing function declarations etc.
* During this stage, the pre-processor statements (the `#include` statements) are processed. This basically means copying the code in the header file into the
source code which includes that header
* Even if a function is just declared and not defined anywhere, the complier will not throw any error as it is the job of the linker to find the signature of the required 
function and link it appropraitely wherever required.

### Linking
* The job of the linker is to stitch together different pieces of the code. Different translation units create different object files upon compilation and then it
becomes the job of the linker to link the approprite function definitions using these object files.
* For instance, consider a simple program which has a `main.cpp` file, a `my_class.cpp` file and a `my_class.h` file.
* The `my_class.h` file contains declarations of different fucntions/classes which we intend to use in the `main.cpp` file.
* The `my_class.cpp` contains the defintions of the functions/classes declared in the `my_class.h` header file. 
* The `main.cpp` files consists of code which uses the objects/functions defined in the `my_class.cpp` file. While compiling `main.cpp`, the compiler will come across
the usage of non-standard/user-defined objects/functions in the code and will throw a compilation error as it does no knows what they exactly do.
* To avoid this compilation error, the header file `my_class.h` is `#include`d in the `main.cpp`. Doing this will copy the declarations from `my_class.h` into `main.cpp`. 
* The same goes for `my_class.cpp` and the `my_class.h` is `#include`d in it as well.
* The files will now compile without errors as the compiler assumes that the declared classes/functions are defined elsewhere.
* That elsewhere is the `my_class.cpp` file. When this file gets compiled, it will be transalated into an object file that contains signatures of different functions and classes.
* When `main.cpp` is comiled and executed, first an object file corresponding to `main.cpp` will be created and then the linker will link the 2 object 
files (corresponding to `main.cpp` and `my_class.cpp`) and will then start executing the program.

#### What happens when we try to include `my_class.cpp` into `main.cpp`?
*
