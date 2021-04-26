# Common Terms

### Widening/Narrowing:
* These are the types of casting in which the value being assigned to an object is not of the same size as that of the object. If the size of the object is smaller/shorter, its called narrowing and if larger, it is called widening.
* For instance casting of float to int is narrowing.

### Scaling (not related to graphics scaling)
* While performing pointer arithmetic, the compiler multiples the integer operand by the size of the object the pointer points to and returns the memory address that many values apart from the pointer. It will not point to the address of the next byte, rather the address of the next object. For instance, 
```C++
int a = 5;
int* ptr = &a;
cout << ptr << endl;
cout << ptr + 1 << endl;
cout << ptr + 2 << endl;
```
The output (indicative) of the above snippet would be
```
0x000000000000
0x000000000004
0x000000000008
```
