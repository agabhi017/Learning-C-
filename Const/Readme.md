## `const`

* The `const` keyword is used to mark any variable or a method as a constant (in case of methods, a const methond wont be able to modify the objects)
* The placement of the const keyword is important to note. Consider the following few examples :
  * `const int a = 5`     (This will set the variable a as a const int type and a program will not be allowed to modify its value)
  * `const int* p = &a`   (This will declare a pointer p which points to a const int type. In sich cases we cannot dereference p and change the value while we can move the pointer p 
  to another variable of type const int)
  * `int const* p = &a` is same as `const int* p = &a`
  * `int* const p = &a`  (This will declare a constant pointer to an integer type and hence cannot be modified to store a different memory address but can be dereferenced to 
  modify the value it points at)
  * `const int* const p = &a`   (This will declare a constant pointer of type const int and hence neither the deferenced value nor its own value can be modified)
* Another place where `const` is used is with methods of a class. Consider the following examples :
  * The following code snippet sets the type of the `func` method as a constant, restricting it to modify the attributes of that class. NO variable can be modified inside the
  definition of the `func()` method.
    ```
    void func() const {
      std::cout << attr;
    }
    ```
  * The return type of the function can be changed to return constant integers or constant pointers as discussed above
    ```
    const int func() const {
      return attr; 
      //return a const int variable
    }
    ```
    ```
    const int* const func() const {
      return attr;
      //returns a constant pointer to a const int data type
    }
    ```
* While passing arguments in a method, once can pass them with the const keyword. This ensures that the method is not allowed to modify the variable. This is used when a 
  variable is passed by a constant reference in a method.
* It should be noted that while accessing member functions using constant references, the function type should be constant as well. This helps to enusre that the
said function does not modifies the object and hence the integrity of the constant reference is held.
  ```
  class a_class{
    int func() const{
      return attr;
    }
  };


  void func(const a_class& object){
    std::cout << object.func();
  }
  ```

    
