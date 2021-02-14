# Virtual Functions in C++


* Virtual functions enable the overwriting of a method in a dervied class. That is a derived class can have a method with the same name as that of the base class 
but can still be modified to run a comlplete different set of instructions. 
* `Virtual` keyword is added as a prefix to the required method name in the base class and the `override` keyword is used as a suffix to the indicate that the member function 
in the derived class is overriding the base-class method.
* This creates a V table or a lookup table which is used to map the correct function to point to after declaring a function as virtual
* An additional cost is associated with the virtual functions in terms of the memory consumption for storing the v table and the run time penalty while looking up the v table
