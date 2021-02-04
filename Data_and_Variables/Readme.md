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
* wchar_t == wide character type. Used to represent the extended character set.
* cin and cout family are not suitable for wchar_t types. The iostream header has wcin and wcout for handling wchar_t type.
* Escape Sequences - \n, \a, \b, \t, \v etc
* Single quotes - character constant, double quotes - part of string


