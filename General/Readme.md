### ___Functions___

* The library files contain the compiled code for the functions, whereas the header files contain the prototypes.
* C++ library functions are stored in library files. When the compiler compiles a program, it must search the library files for the functions you’ve used. Compilers differ on which library
files they search automatically.
* Compilers like to add an underscore prefix to function names—another subtle reminder that they have the last say about your program.
* Note that unlike some computer languages, in C++ you must use the parentheses in the function call even if there are no arguments.
* Some languages reserve the term function for functions with return values and use the terms procedure or subroutine for those without return values, but C++, like C, uses the term function for both variations.
* main()’s return value is returned not to another part of the program but to the operating system. For example, Unix shell scripts and Window’s command-line interface
batch files can be designed to run programs and test their return values, usually called exit values.
* The normal convention is that an exit value of zero means the program ran successfully, whereas a nonzero value means there was a problem. Thus, you can design a C++
program to return a nonzero value if, say, it fails to open a file.You can then design a shell script or batch file to run that program and to take some alternative action if the program signals failure.
* Incidentally, main is not a keyword because it’s not part of the language. Instead, it is the name of a required function. You can use main as a variable name (but that can cause some problems apart from making the program confusing).
* 
