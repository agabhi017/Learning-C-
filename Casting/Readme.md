# Casting

Casting can be broadly classified into two types :
  * Implicit casting (implicity converting the data type of a variable by for instance copying into a variable of another type such as float to int etc.)
  * Explicit casting (explicitly indicating the compiler to cast the data type of a variable into something else)
There are multiple types of casting supported in C++ :
  * C-style casting. For example  :
    * ```C++
      float a = 5.5;
      int b = (int)a;
      ```
      The usage of `(int)` is referred to as C-style casting
  * C++ style casting :
    * `static_cast  <typename>`
    * `dynamic_cast <typename>`
    * `const_cast <typename>` (add/remove the const qualifier)
    * `reinterpret_cast <typename>` (re-interpret the given memory address as something else also known as `type punning`)
  * C-style casting is generally able to achieve whatever C++ style casting is able to achieve but the latter has added advantages over the other:
    * Added checks at compile time 
    * Easy to lookup instances of casting in the codebase thus facilitating debugging       
