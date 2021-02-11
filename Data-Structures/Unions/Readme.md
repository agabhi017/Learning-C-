# Unions

* A `union` is a user-defined data type in which all the memmbers(member variables) share the same memory and can only store one of the members from the list. 
* Thus the memory occupied will be equal to the size of the largest member in the defined structure.

The following snippet shows an example of union data type. 

```c++
// declaring_a_union.cpp
union RecordType    // Declare a simple union type
{
    char   ch;
    int    i;
    long   l;
    float  f;
    double d;
    int *int_ptr;
};

int main()
{
    RecordType t;
    t.i = 5; // t holds an int
    t.f = 7.25; // t now holds a float
}
```
