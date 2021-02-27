# Smart Pointers

`std::unique_ptr`  `std::weak_ptr`  `std::shared_ptr`

* Smart pointers are a way to automate memory management. While using the `new` keyword, one need to ensure calling the `delete` keyword to free up the memory
and avoid memory leakage issues.
* However smaprt pointers provide a way to automate this process without having to worry about de-allocating the memory manually.
* These pointers can be used by including the `memory` header file.
* There are 3 kinds of smart pointers - `unique`, `shared` and `weak`.
* The `std::unique_ptr` is a scoped pointer and wil be automatically deleted when it goes out of scope. Also as the name suggests, it is a `unique` pointer which 
means that it cannot be copied.
* If one were to copy a `unique` pointer, that would actually make 2 pointers poiniting to the same location in the memory. So when one of the pointer goes out of scope 
and is deleted, the other pointer now points to a memory which has been freed already! Hence unique pointers cannot be copied.
* If one neds to copy pointers, we can used `shared` pointers instead. These pointers keep an internal `reference count` of how many pointers are referencing the same 
memory and are deleted once the reference count drops to zero.
* The `shared` pointers have an overhead as they allocate extra memory to keep the reference count. 
* One can construct the shared pointer by explicitly calling the constructor and using the `new` keyword, but doing so will result in two allocations. One for the object 
itself which is called by the user and another one for the `ref count` called by the pointer. This is less efficient than allocating the combined memory together at one place. 
* In case one does want an ownership of the object and does not want the shared pointer to increase the `ref count`, `weak` pointers can be used.
* These are more of a reference in case when we only need a ref to an object and do not want to own it.

A nice article on smart pointers vs `new` and `delete` :

https://bromeon.ch/articles/raii.html
