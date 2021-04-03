# Inline Functions

### What are inline functions
* To understand inline functions better, first lets understand how the program is executed after we hit compile.
    * First, the compiler creates an executable file which contains machine instructions
    * Secondly, these instructions are loaded into the memory and are executed one-by-one or rather line by line
    * As the program may contain loop or functions, program execution may jump over to another memory address (for instance memory address of a function), execute it and return back 
      to the original sequence. In such cases the computer stores the memory address of the instruction which follows the fucntion call so that it can return back to this address 
      to continue executing the original program
* Such jumping back and forth and keeping track of where to resume from adds an overhead cost and the program maybe slowed down depending on the number of function calls and the 
  program design
* The next thought which immediately pops up about optimizing the performance is how to reduce the number of hops. This is where `inline` comes into picture.
* Using `inline` qualifier is same as asking the compiler to replace the function call with the correspoding function code. Whenever compiler sees a function call to an inline 
  function it will replace that with the code/instructions inside that function.
* While using the `inline` keyword may seem to reduce the number of memory hops a computer has to make but it may have its ows costs as well. Consider a case where a function is
  too long or in other words does a bunch of things other than simply printing to the console, using `inline` would mean copying that entire chunk of code inside the program 
  which will increase the memory cost

### When to use inline functions then?
* If the function is doing petty things like returning the square of a number of adding them up, it will be better to have them treated as inline. In other terms consider these 
  two costs before coming at a decision :
    * Cost to exeute the code inside the function (lets call this as `function_cost`)
    * Cost to handle the mechanism of fucntion calls and memory hops (lets call this one as `program_cost`)
* Now there can be 2 scenarios :
    * function_cost > program_cost : In this case we can give up on the `inline` function call as it will be a lager memory overhaed to have several copies of a large function 
      inside the program
    * program_cost > function_cost : In this case as the function is relatively "smaller", it can be treated as an inline function as it will hurt more to do memory hops
* There are other cases where a compiler may not obey the inline qualifier. These can be :
  * If a fucntion calls itself (recursion)
  * If a function is too large <br/>
  In such cases the compiler may disregard the inline keyword and implement the functions as regular functions.
    
### Diff b/w inline functions and C style macros
Apart from multiple syntactical and functional differences, here is one interesting example of diff b/w an inline function and a macro as the seemingly do similar things - 
replacing certain piece of code in a program by something else.
* C style macros which are defined uising the `#define` keyword work basically by text substitution. They are not actual functions but just behave in a similar way, not in the
  same way.
* Consider the following beautiful example covered in the C++ primer book :
  ```C++
  #define SQUARE(X) X*X
  inline double square(double x) { return x * x; }
  
  int main(){
    double c = 13.0;
    a = SQUARE(5.0); //is replaced by a = 5.0*5.0;
    b = SQUARE(4.5 + 7.5); //is replaced by b = 4.5 + 7.5 * 4.5 + 7.5;
    d = SQUARE(c++); //is replaced by d = c++*c++;
    e = square(c++); //is replaced by square(c) and then increments c after function termination
  }
  ```
* As observed, functions allow us to pass expressions as arguments. These expressions will be evaluated first and then the function will be executed. 
    * For isntace `square(c++)` will execute the function for the current value of c and will incerement it by one once the function terminates
    * On the other hand `SQUARE(c++)` will be replaced by c++*c++ as per the macro definition. In this case c will be incremented twice after the macro is executed.
      Moreover, the result will not be the same as `square(c++)`, but will rather effectively behave as `c*(c + 1)`
  
