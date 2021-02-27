# Enumerated Types or ENUMS

* In a very crude from ENUMS are just integers. Overloading a syntax on top of integers such that they can take only certain values are called ENUMS.
* In simple words, ENUMS are a custom data type where one can restrict the values which an ENUM object can take. Consider the following example:
```
enum my_enum{
  a, b, c
}
```
* This restricts the objects of type my_enum to take only one of 3 values - a, b or c.
* By default, the first value in the enum is assigned the value 0 and then each value is incremented by one.
* This behavior can be modified by assigning the values inside the ENUM definition directly. 
* Since it is just an integer, we can access the variables a, b, and c outside the scope of enum as well (after proper name resolution).
