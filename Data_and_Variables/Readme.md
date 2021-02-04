[Reference - C++ Primer Book]

### ___Names of Variables___

* The only characters you can use in names are alphabetic characters, numeric digits, and the underscore (_) character.
* The first character in a name cannot be a numeric digit.
* Uppercase characters are considered distinct from lowercase characters.
* You can’t use a C++ keyword for a name.
* Names beginning with two underscore characters or with an underscore character followed by an uppercase letter are reserved for use by the implementation—that is, 
the compiler and the resources it uses. Names beginning with a single underscore character are reserved for use as global identifiers by the implementation. For example names such as \_\_my_var is a legal name and will not result in compilation error, but may produce unexpected behavior as such type of variables names are reserved for the implementations to use.
* C++ places no limits on the length of a name, and all characters in a name are significant. However, some platforms might have their own length limits (jn ANSI C(C99) ony the first 63 characters of the variable name are considered to be significant and the variables with the same first 63 characters will be treated as the same irrespective of the following characters).

### ___Integer Types___

* "Width" is the usual term for describing the amount of memory used for an integer.
* Int types in the increasin order of width are char, short, int, long. long long (each with both signed and unsigned versions).
  * A short integer is at least 16 bits wide.
  * An int integer is at least as big as short.
  * A long integer is at least 32 bits wide and at least as big as int.
  * A long long integer is at least 64 bits wide and at least as big as long.
* The manipulators "hex", "ct" can change the way cout displays integers. Use cout << maipulator_type; to change the notation of the integer type.
* The cout.put() member function provides an alternative to using the << operator to display a character.

### ___Characters___

* The ASCII code is incorporated as a subset of Unicode, so U.S. Latin characters such as A and Z have the same representation under both systems.
* Unicode assigns a number, called a code point, for each of its characters. The typical notation for Unicode code points looks like this: U-222B. The U identifies this as a Unicode character, and the 222B is the hexadecimal number for the character—an integral sign, in this case.
* Characters can be signed or unsigned and depends on the usage. If we want to hold numerical values in a char variable we can define it to be signed or unsigned as per the range of desired values.
* NOrmal characters are 8 bits, i.e., we can have 256 characters representations in decmal form ranging from 0 to 255. However as we continue to extend the base of the characters, more space is needed to represent them. Hence the type wchar_t was introduced.
* wchar_t == wide character type. Used to represent the extended character set.
* cin and cout family are not suitable for wchar_t types. The iostream header has wcin and wcout for handling wchar_t type.
* Escape Sequences - \n, \a, \b, \t, \v etc
* Single quotes - character constant, double quotes - part of string
* As the character space continues to grow, wchar_t wasnt enough and char16_t and char32_t were introduced which are unsigned 16 and 32 bits respectively.
* The 'u' prefix is used for char16 and 'U' for char32. char16 is typically of the form \u00F6 while char32 is of the form \U0000002B.

### ___Constants___

* Constants are declared and initialized using the const qualifier. Its called a qualifier as it qualifies the  meaning of a declaration.
* Read only type and cannot be modified in the subsequent parts of the code.
* Differences with the #define statement :
 * Lets you specify the type explicitly
 * Can use scoping to limit the definitions to certain files/functions
 * Can use with other data types such as arrays/structures

### ___Floating Points___

* These values are stored in 2 parts - value and the scaling factor. The value stores the numbers disregarding the decimal point while the scaling factor stores the information for the decimal point in the form of a factor (e.g. 100 on a base of 10)
* The scaling factor serves to move the decimal point, hence the name - floating point numbers.
* E notation guarantees that a number is stored in floating-point format, even if no decimal point is used. However, you can’t have spaces in the number, so, for
example, 7.2 E6 is invalid.
* three floating-point types: float, double, and long double
* float is 32 bits, double is 64 bits, and long double is 80, 96, or 128 bits
* Normally cout drops trailing zeros. For example, it would display 3333333.250000 as 3333333.25.The call to cout.setf() overrides that behavior. "cout.setf(ios_base::fixed, ios_base::floatfield)"
* cout prints six figures to the right of the decimal
* By default, floating-point constants such as 8.24 and 2.4E8 are type double. If you want a constant to be type float, you use an f or F suffix.
* type float can represent only the first 6 or 7 digits in a number, so trying to change the 23rd digit has no effect on the value.

### ___Arithmetic Operators___

* the % operator works only with integers
* When two operators have the same precedence, C++ looks at whether the operators have a left-to-right associativity or a right-to-left associativity.
* Left-to-right associativity means that if two operators acting on the same operand have the same precedence, you apply the left-hand operator first. For right-to-left
associativity, you apply the right-hand operator first.
* The process of using the same symbol for more than one operation is called operator overloading.



