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

```C++
enum Foo { a, b, c = 10, d, e = 1, f, g = f + c };
//a = 0, b = 1, c = 10, d = 11, e = 1, f = 2, g = 12
```

### Unscoped Enums

### Enum Classes (Scoped Enums)
* C++11 allows us to define enum classes over regular enums due to some of the limitattions of the enum type :
  * Two enums cannot share variable names
  * We cannot declare a variable with the same name as that included in the enums
  * Enums are not `type-safe`. They allow implicit conversion as the default values in the enum start from 0. Consider the following code snippet :
  ```C++
  enum Gender { Male, Female };
  enum Color { Red, Green };

  Gender gender = Male;
  Color color = Red;

  if (gender == color)
      cout << "Equal";
  ```
  The output will be "Equal" as both of the varaibles have the same value 0.
* Hence, the enum classes are are both strongly typed and strongly scoped. Find more examples [here](https://www.geeksforgeeks.org/enum-classes-in-c-and-their-advantage-over-enum-datatype/)
