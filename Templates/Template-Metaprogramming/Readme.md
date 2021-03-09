# Template Metaprogramming

* Template metaprogramming is a concept where we can use templates to perform computations at compile time. 
</br>
For instance, the function for finding the factorial can be written in a non-templated way as :

``` C++
unsigned int factorial(unsigned int n) {
	return n == 0 ? 1 : n * factorial(n - 1); 
}
```

The same can be achieved using metaprogramming :
``` C+++
template <unsigned int n>
struct factorial {
	enum { value = n * factorial<n - 1>::value };
};

template <>
struct factorial<0> {
	enum { value = 1 };
};
```
* The templated code will be 'unrolled' at the compile time to evaluate the factorial given any n. (This n must be known to the compiler at compile time)
* Since the computations are done at compile time, the code becomes similar to int factorial_4 = 24 (upon instantiating factorial<4>).
* However this optimization is relatively minor, it can make a big difference when the compiler actually unrolls loops. For instance :

```C++
template <int length>
Vector<length>& Vector<length>::operator+=(const Vector<length>& rhs) 
{
    for (int i = 0; i < length; ++i)
        value[i] += rhs.value[i];
    return *this;
}
```

When the compiler instantiates the template, the following code might be produced :

```C++
template <>
Vector<2>& Vector<2>::operator+=(const Vector<2>& rhs) 
{
    value[0] += rhs.value[0];
    value[1] += rhs.value[1];
    return *this;
}
```

As the `length` is constant at run time, the compiler's optimizer should be able to unroll the for loop.

