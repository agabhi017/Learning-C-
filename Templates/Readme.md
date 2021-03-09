# Templates in C++

* In simple terms templates are used to 'standardize' or 'templatize' the code wherein we can avoid writing duplicate lines of code with only minor changes
such as overloading a same function with different typenames (for example, a print function with separate definitions for each typename).
* The syntax is `template<whatever_is_to_be_templatized name_of_that_template, ...>`
  * `template<typename T>`
  * `template<int Num>`
  * `template<class CL>`
* Usage :
```C++
template<typename T, int Num>   // note that the semicolon is not used here which makes this a part of the next line
class my_class(){
  private:
    T my_arr[Num];   // using any other variable for sizing the array would result in a compile error as the stack needs  
};                   // to know the size which it needs to allocate at the compile time

int main(){
  my_class<int, 17> arr;
}
// The above template will allow us to create an array of any default typenames in C++ and of size which is defined 
// at the compile time.
```
* The templatized lines of code are generated at compile time as and when the user calls them. The templates instructs the compiler to write the code for us depending on 
the input. For instance, in the above code block passing 'int and 5' as inputs will direct the compiler to generate the code which will create a class definition with
integer array of size 17 as a private member.
* Since such blocks of lines are generated when a user requests them by passing arguments, they are not compiled until and unless they are called. So the code will compile
fine if the above templatized class definition had syntactical arrors but was never instatntiated by the user.
* Each variation in the template arguments will create a separate definition at compile time. Hence, each of the definition will have their own copies of static members if
declared. These static members will now belong to a templatized class with particular arguments.

### Template Sepcialization and Preference order 

Consider the following code block :
```C++
#include <iostream>
using namespace std;

template <class T>
void fun(T a)
{
   cout << "The main template fun(): "
        << a << endl;
}

template<>
void fun(int a)
{
    cout << "Specialized Template for int type: "
         << a << endl;
}

void fun(int a)
{
    cout << "Non templated function: "
         << a << endl;
}


int main()
{
    fun<char>('a');
    fun(10);
    fun<int>(10);
    fun<float>(10.14);
}
```
The above block contains:
  * A templated function defintion (1st definition)
  * A specialized templated function defintion for a certain data type (2nd definition)
  * A non templpated function defintion with the same name and number of arguments as the first two

Upon encountering calls to the function `fun` the compiler will look for function definitions in the following order:
  * A non templated function defintion (for instance in cases when a user wants to handlw a particular data type separately from the templated set) (3rd definition)
  * Most specialized templated fucntion definition (in this case the 2nd definiton)
  * Any generalized templated definition (1st defintion)
  
Hence, the output of the above program will be :
```
The main template fun(): a
Non templated function: 10
Specialized Template for int type: 10
The main template fun(): 10.14
```

### Template Metaprogramming
[Read the details here](https://github.com/agabhi017/Learning-Cpp/tree/main/Templates/Template-Metaprogramming)

### Questions :
* In the first codeblock the my_arr is private to the class. How are we able to access it directly from the main without any helper functions?
Ans: </br>
None of the templatized code exists until and unless its instantiated. For instance, in the example code block, none of the lines for the class defintion would exist at
compile time if it was not called from main. Calling/instatntiating will direct the compiler to first write the class defintion with the given template arguments
and then it will be compiled. So only after after instatiation, the 'public/private' members will come into play. 
