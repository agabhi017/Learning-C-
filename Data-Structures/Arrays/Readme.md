# Arrays (not `std::array`)

* Arrays are compound data types or data structures that can hold multiple values of a same type.
* They allow random mamory access as the elemnts of the array are stored in a contiguous memory block thus allowing "easy" or constant time access to any elemnt of the array.
* The synatx for declaring an array is `typename arrayname[size]`. For example an array of 5 ints will be defined using `int arr[5]` where arr is the name of the array.
* The size which an array holds in the memory will thus be `arraysize * sizeof (typename)`. For the example in the above line, `sizeof(arr) = 20 bytes`.
* The elements of an array can be accessed by indexing using `[]`. It is important that the index used to access an array element is well within the array size as the C++ compiler does not check for valid subscripts and accessing an element outisde of the array size would result in undefined behavior and might also corrupt data stored at other memory locations.
* `Important` For an array which is to be allocated on the stack memory (not heap), as per the standards, the size of the array must be known at the compile time itself. Consider the following cases:
```C++
int arr[5];     //perfect, allowed
int arr[];      //not allowed as we need to declare the size
int arr[size];  //if size is already defined => accepted otherwise if determined at compile time => not allowed as per ISO
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
* If an array is uninitialized, its elements are undefined and may contain the values previously stored at those addresses.
* `Array Initialization`
```C++
int cards[4] = {3, 6, 8, 10};     //allowed
int hand[4];                      //allowed, uninitialized array
hand[4] = {5, 6, 7, 9};           //not allowed; list-initialization only at the time of array declaration
hand = cards;                     //not allowed, we will see later why so
float hotelTips[5] = {5.0, 2.5};  //allowed, the rest of the values are set to zero
long totals[500] = {0};           //sets all the values of the array to 0
long totals[500] = {1};           //only the first element is 1, rest all are set to 0
short things[] = {1, 5, 3, 8};    //the compiler will deduce the size of the array
```
C++ style:
```C++
double earnings[4] {1.2e4, 1.6e4, 1.1e4, 1.7e4};    //list-initialization
unsigned int counts[10] = {};                       //all elements set to 0
float balances[100] {};                             //all elements set to 0
long plifs[] = {25, 92, 3.0};                       //not allowed; narrowing not allowed in list-initialization
char slifs[4] {'h', 'i', 1122011, '\0'};            //not allowed; narrowing
char tlifs[4] {'h', 'i', 112, '\0'};                //allowed; 112 within the char range
```
* As array elements are stored in a contiguous block of memory, storing elements in a 1D array of size say 9 might be same as storing in a 2D array of size 3X3. For instance, 
```C++
int arr[3][3] = {{1,2,3}, {4,5,6}, {7,8,9}};
//this array is stored in the memory as :
0x61fd70        1
0x61fd74        2
0x61fd78        3
0x61fd7c        4
0x61fd80        5
0x61fd84        6
0x61fd88        7
0x61fd8c        8
0x61fd90        9
//The order will be same in the memory if we instead had
int arr[9] = {1,2,3,4,5,6,7,8,9};
```
Note that the addresses of the elements are 4 apart from each other as the size of int is 4 bytes and the lowest memory address is assigned as the address of the whole object.
* `Array Decay` - when a fixed array is implicitly converted to a pointer that points to the first element of the array. There are only few cases when the arrays are not decayed by default: arrays in structs and classes do not decay.
```C++
int arr[2] = {1,2}; //both &arr[0] and arr store the address of the first element of the array.
```
* `Important` - array decay is only an implicit conversion. The compiler does not create a separate pointer variable by the name of the array that stores the address of the first element in the array. Name of the array just becomes a short-hand for &arr[0].
* Once array decay occurs, we can also use pointer arithmetic to traverse the elements of the array in addition to the subscripting syntax. We just increment the pointer and de-reference it to get the value.
* Pointer arithmetic in case of multi-dimensional arrays can be understood by breaking down the arrays as arrays of arrays.
```C++
int arr1[3];        //array of 3 integers
int arr2[3][3];     //array of 3 1D arrays of size 3
int arr3[3][3][3];  //array of 3 2D arrays of size 3*3

int arr1[3];        //arr1 points to arr1[0]
int arr2[3][3];     //arr2 points to arr2[0][0]; 
                    //*arr2 points to the first 1D array out of the 3; 
                    //**arr2 == arr2[0][0]
int arr3[3][3][3];  //arr3 points to arr3[0][0][0]; 
                    //*arr3 points to the first 2D array out of the 3 2D arrays; 
                    //**arr3 points to the first 1D array of the 3 1D arrays in the first 2D array out of the 3 2D arrays
                    ///***arr3 = arr3[0][0][0]

int* ptr1 = arr1;            //as arr1 points to an integer; pointer to an integer
int (*ptr2)[3] = arr2;       //as arr2 points to a 1D array of size 3; pointer to an array of 3 ints
int (*ptr2)[3][3] = arr3;    //as arr3 points to a 2D array of size 3*3; pointer to a 2D array of 3*3 size

sizeof arr    == 3*3*3*4 bytes == 108 bytes  //3D array of ints
sizeof *arr   == 3*3*4 bytes   == 36 bytes   //2D array of ints
sizeof **arr  == 3*4 bytes     == 12 bytes   //1D array of ints
sizeof ***arr == 4 bytes                     //integer
```
* Since `arr` is not an explicit pointer, `sizeof arr` returns the entire size of the array object in the memory. Had `arr` been an explicit pointer, `sizeof arr` would return 8 bytes on a 64-bit machine and 4 bytes on a 32-bit machine which corresponds to the size pointers occupy in memory.
* `Passing arrays to functions` Passing variables by values results in the creaation of a copy of that variable but in the case of an array, a copy is not created. Instead, the actual array is passed to the function in the decayed form, i.e., as a pointer. 
* Once an array is passed as a pointer in the decayed form to a function, there is no way for a function to determine the size of the original array. To retrieve the size, an additional parameter has to be passed to the function. If we try to use the `sizeof` operator we will only get the size a pointer occupies in the memory. A properly designed compiler should throw a warning if we try to use `sizeof` on the array passed into a function.
* The arrays passed in the functions can be modified as a pointer is passed. We can use subscripting syntax or pointer arithmetic to access the elements of the array. If we do not want to modify the array, pass it using a `const` qualifier instead.
* There are 2 ways in which we can pass an array to a function:
```C++
void func(int* array);
void func(int array[]);

void func(int array[][]);     //not allowed as we can only get away with not specifying one of the dimensions at maximum
void func(int array[][5]);    //allowed
```
