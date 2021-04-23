# Macros

### C-style Macros
* C style macros are defined using the `#define` directive and work by replacing 'text' into the macro definition. Consider the following code snippet:
```C++
#define square(x) x*x
#define SQUARE_(x) (x) * (x)

int main(){
    int c = 13;
    int a = 13;
    cout << square(c++) << endl;      //return c*(c + 1) and increments c twice after execution //13*14
    cout << SQUARE_(a++) << endl;     //returns the same as above
    cout << square(2 + 3) << endl;    //returns 2 + 3*2 + 3 = 2 + 6 + 3 = 11 as it only replaces text
    cout << SQUARE_(2 + 3) << endl;   //returns (2 + 3)*(2 + 3) = 25
    return 0;
}
```
* These types of macros suffer when we pass an expression as an argument. As these are not functions, they just treat the expression like text and replace them into the macro definition. To provide a better safety for expressions we can use parenthesis for evaluating the arguments first and then executing the macro definition.
