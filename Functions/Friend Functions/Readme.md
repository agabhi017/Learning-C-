# Friend Functions

* Friend functions are 'special' functions that have the same access to a class's members as the member functions themselves.
* These functions are not scoped by the class definition but are declared inside the class to which they are a friend to.
* One common application of friend functions are operator overloaders. Consider the following snippet :
```C++
class A{
  int a;
public:
  A(int x) : a(x){}
  int operator+ (int x){
    return a + x;
  }
};

int main(){
  A aa(5);
  int a = aa + 2; //works fine and a = 7
  return 0;
}
```
* The instruction aa + 2 is same as aa.operator+(2). Since this behavior is well defined by the class definition by overloading the '+' operator, the result is deterministic.
* But what if we instead wrote 2 + aa. This will result in compilation error as 2 is not an object of class A and we have only overloaded the '+' operator which implicitly takes the left operand of the '+' operator as the first argument and the second is explicitly passed to the overloader function. Since there is no definition of 2.operator+(aa) we get a compilation error.
* One possible work-around is to use a separate operator overloading which handles these cases. Since in such cases we may need to access the private data members, we will now declare a friend function inside the class definition. The code snippet will now look as follows :
```C++
class A{
  int a;
public:
  A(int x) : a(x){}
  int operator+ (int x){
    return a + x;
  }
  friend int operator+ (int a, const A& obj);
};

int operator+ (int a, const A& obj){
  return a + obj.a;
}

int main(){
  A aa(5);
  int a = aa + 2; //works fine and a = 7
  int b = 2 + aa; //this now works fine as well with b = 7
  return 0;
}
```
* The friend operator+ function has acceess to the private data member 'a' of the class A and hence can be used directly inside the fucntion definition.
* While it may look that the friend functions defeat the purpose of encapsulation and OOP by providing access to external functions, it should be kept in mind that the class designer has total control over what functions can be friend to a particluar class. Hence, the friend functions in some way provide an extension the OOP interface.
* Although the above example can be solved in a different way without using friend functions, its purpose was to showcase their usage. However, in some cases, using non-member friend functions might be helpful over member functions. (TBC)
