# Arrays

* Arrays are compound data types or data structures that can hold multiple values of a same type.
* They allow random mamory access as the elemnts of the array are stored in a contiguous memory block thus allowing "easy" or constant time access to any elemnt of the array.
* The synatx for declaring an array is `typename arrayname[size]`. For example an array of 5 ints will be defined using `int arr[5]` where arr is the name of the array.
* The size which an array holds in the memory will thus be `arraysize * sizeof (typename)`. For the example in the above line, `sizeof(arr) = 20 bytes`.
* The elements of an array can be accessed by indexing using `[]`. It is important that the index used to access an array element is well within the array size as the C++ compiler does not check for valid subscripts and accessing an element outisde of the array size would result in undefined behavior and might also corrupt data stored at other memory locations.
* `Important` For an array which is to be allocated on the stack memory (not heap), as per the standards, the size of the array must be known at the compile time itself. Consider the following cases:
```C++
int arr[5];     //perfect, allowed
int arr[];      //not allowed as we need to declare the size
int arr[size];  //if size is already defined ==> accepted otherwise if determined at compile time ==> not allowed as per the standards
```
However, some compilers do allow varible sized arrays but it should be noted that it might not always be portable. If one needs dynamicaally sized arrays use heap allocators or the `vector` STL class.
* The name of the array is the memory address of the first element of the array, that is it acts as a pointer to the first element of the array. 
* These arrays can be multi-dimensional and then with the addition of each dimension, the array becomes an array of smaller arrays.
```C++
int arr[5];       //1D array of size 5
int arr[5][5];    //2D array of size 5*5
int arr[5][5][5]; //3D array of size 5*5*5
int arr[][5];     //not allowed as the size should be determined at compile time
```
