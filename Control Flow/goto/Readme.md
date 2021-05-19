# goto and statement

* The `goto` control statement is used for jumping around in a code. It is coupled with a `statement` which contains the statements to execute to once jumping to that location.
* We can jump forward/backward in a code and we do not need to provide a 'prototype' as it has a `function` scope. This means that we can use the `goto` keyword even before defining what the corresponding statement 'means'.
* We cannot skip over any variable declarations/initializations that will be further used inside the `statement` block.
* We can only jump within a function and not to a location outside the function where `goto` is used.
* A typical example looks like:
```C++
int main()
{
    double x{};
tryAgain: // this is a statement label
    std::cout << "Enter a non-negative number: "; 
    std::cin >> x;
 
    if (x < 0.0)
        goto tryAgain; // this is the goto statement
 
    std::cout << "The square root of " << x << " is " << std::sqrt(x) << '\n';
    return 0;
}
```
* In most cases, this should be avoided at all costs unless there is no cleaner alternative way of achieveing the same thing.
