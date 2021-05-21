# `std::exit`

* First, lets try to understand what happens when a program executes normally, i.e., when we reach the end of the main function
  * All the local variables and function parameters are destroyed
  * A special function called `std::exit` is called with the return value from the main as the function parameter.
  * The `std::exit` function causes the program to terminate normally and does some cleanups such as destroying objects with static duration and some misc. file cleanup
  * It then returns the control back to the OS with the function paramater as the `status code`
* Under normal circumstances, `std::exit` is called implicitly, but it could also be called explicitly to halt the program earlier. An example usage is:
```C++
#include <cstdlib> // for std::exit()
#include <iostream>
 
void cleanup()
{
    // code here to do any kind of cleanup required
    std::cout << "cleanup!\n";
}
 
int main()
{
    std::cout << 1 << '\n';
    cleanup();
 
    std::exit(0); // terminate and return status code 0 to operating system
 
    // The following statements never execute
    std::cout << 2 << '\n';
 
    return 0;
}
```
* This `std::exit` function can be called from any function and not only main to terminate the program
* `Important`: Since in normal cases the cleanup of local variables is done before `std::exit` is called, even if we call it explicitly, this cleanup will not be done, and the burden is on the user to configure a cleanup function that can be called when `std::exit` is used.
* To ease this out, we have an additional function called `std::atexit` which lets the user pass the names of the cleanup functions as paramaters which will be called in the reverse order (last argument to first). This provides a little convenience, as we need not remember to call the cleanup function separately always.
* The arguments passed to `std::atexit` will be called even if the `std::exit` is called implictly. Also the functions passed in as arguments must not take any input neither have any return value.
* There are other type of halts such as `std::abort` and `std::terminate` which we will cover later.
* We should almost never use a halt unless there is no other safer way to exit from the program.
