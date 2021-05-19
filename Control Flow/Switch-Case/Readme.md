# Switch Case statements

* Switch case statements are alternatives to if-else blocks with certain limitations and advantages.
* The syntax for using switch-case statement is:
```C++
void printDigitName(int x)
{
    switch (x) // x is evaluated to produce value 5
    {
        case 1:
            std::cout << "One";
            return;
        case 2:
            std::cout << "Two";
            return;
        case 3:
            std::cout << "Three";
            return;
        default: // which does not match to any case labels
            std::cout << "Unknown"; // so execution starts here
            return; // and then we return to the caller
    }
}
```
* The one noticebale difference between switch-case and if-else is the return value of the expression being tested. In if-else statements there is no limitation on the data type of the expression, but for the switch case statement, the output should always be an integer, which is one of the limitations. 
* Another noticeable difference is the use of the `return` keyword inside each of the cases which mide add slightly more effort while writing code as compared to if-else blocks.
* We do not need braces to scope each of the case blocks and it can contain multiple statements unlike the single statement in the if-else case (without braces). The statements after the labels are all scoped to the switch block and no implicit scope is created.
* A major advantage of switch-case is the efficiency in execution. While in the if-else blocks, the expression is evaluated for each branch (unless we meet a condition and exit), in switch-case blocks, the expression is evaluated only once and each of the case is then acceessed using array like indexing or via jump tables to be precise, making the execution much faster.
* There is no practical limit to the number of case lables which can be used, but there should not be any duplication amongst those labels.
* We can also use `break` statement to exit the switch-case block. In the above example, the `return` statement exits the entire function upon execution of the conditionals. 
* But why do we need a `break` or a `return` statement? Whenever one of the conditions is met, the program execution starts from that point and terminates only when one of the following condition is met:
  * The end of the switch-case block
  * Encountering other control flow statements, typically return or break
  * Something else interrupts the normal execution of the program, like OS malfunction etc
* Hence, once a 'case' is executed, the execution will overflow into other 'cases' as well unless we 'break' out of the execution. This behavior is termed as `fallthrough`.
* The `[[fallthrough]]` attribute: C++17 introduced a new `[[fallthrough]]` attribute (which should be used in conjunction with the null statement(;)) to indicate intended fallthrough. For example:
```C++
int main()
{
    switch (2)
    {
    case 1:
        std::cout << 1 << '\n';
        break;
    case 2:
        std::cout << 2 << '\n'; // Execution begins here
        [[fallthrough]]; // intentional fallthrough -- note the semicolon to indicate the null statement
    case 3:
        std::cout << 3 << '\n'; // This is also executed
        break;
    }
 
    return 0;
}
```
* There might be some use cases where we may skip `break` or `return` for each of the cases. Consider the following example:
```C++
bool isVowel(char c)
{
    switch (c)
    {
        case 'a': // if c is 'a'
        case 'e': // or if c is 'e'
        case 'i': // or if c is 'i'
        case 'o': // or if c is 'o'
        case 'u': // or if c is 'u'
        case 'A': // or if c is 'A'
        case 'E': // or if c is 'E'
        case 'I': // or if c is 'I'
        case 'O': // or if c is 'O'
        case 'U': // or if c is 'U'
            return true;
        default:
            return false;
    }
}
```
In the above example, if any of the case matches, the execution will continue until the last case and return true and since each of the previous cases do not have any statements we do get the intended result. This is not considered to be a fallthrough behavior, rather its stacking of different case lables.
* `Variable declaration and initialization`: We can declare (but not initialize) variables inside a switch both before and after case labels. Variables defined in once case can be used in later cases even if that case is not executed. This is because, declaring variables direct the compiler that a variable is created in that scope but initilaiznf 
* The individual cases are not tightly scoped, that is the cases share the same scope unless any of them is explicitly scoped using braces. In such case, the variables deifned inside that scope will not be available to other case blocks.
* 



