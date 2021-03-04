# Vecotrs(Dynamic Arrays)

* Vectors (`std::vector`) are dynamic arrays that expand in size once they get used up. 
* While resizing, they allocate a new memory which is usually double the size of the previous vector and copies the content from old one into the new location and frees the previous 
chunk of the memory.
* During allocation and re-allocation of memory, there are a lot of copying steps involved which copy the objects from one memory location to another. 
* Different types of copying processes while using vectors are :
  * copying an object from the `main` stack to the vector container.
  * copying the contents of the old vector into a newer vector of a larger size. 
* This step can be optimized by asking the vector to reserve a given space before hand so that re-sizing or reallocation of memory is not required.
* There are 3 ways in which we can define the size of our vetor.
  * First - indicating the size while declaring the vector. For example, `std::vector <my_object> my_vector(n)`. 
    * An important point to note about this is that the vector actually constructs n instances of my_object class. So this is to be used only when 
    we want to construct objects and we have a well defined constructor.
    * Using `push_back` will add new element(s) after constructing the first n elements. That is, the index of this element will be `n` (and not 0).
  * Second - using `resize`. It is the same as the first option, but just differs in the aspects of function calls. This can be used whenever we want to change the size of the 
  vector and not necessarily declaring the size when declaring the vector itself.
  * Third - using `reserve`. This will direct the vector to allocate the given size of the memory and then we can use the `push_back` command to fill out the vector (starting 
    from the index 0).
* Another optimization which can be done apart from `resize` or `reserve` is by using `emplace_back`. Since we first construct an object in a function stack (usually 
the main stack), we copy this instance to the vector container. Using `emplace` we can construct the object directly inside the container thus avoiding the copying of objects 
from the function stack
