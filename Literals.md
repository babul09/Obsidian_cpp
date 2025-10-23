#unit5 
[[Constant Variables]]

**Literals** are values that are inserted directly into the code. For example:

```cpp
return 5;                     // 5 is an integer literal
bool myNameIsAlex { true };   // true is a boolean literal
double d { 3.4 };             // 3.4 is a double literal
std::cout << "Hello, world!"; // "Hello, world!" is a C-style string literal
```
Literal suffixes

If the default type of a literal is not as desired, you can change the type of a literal by adding a suffix. Here are some of the more common suffixes:

| Data type      | Suffix                                 | Meaning                                   |
| -------------- | -------------------------------------- | ----------------------------------------- |
| integral       | u or U                                 | unsigned int                              |
| integral       | l or L                                 | long                                      |
| integral       | ul, uL, Ul, UL, lu, lU, Lu, LU         | unsigned long                             |
| integral       | ll or LL                               | long long                                 |
| integral       | ull, uLL, Ull, ULL, llu, llU, LLu, LLU | unsigned long long                        |
| integral       | z or Z                                 | The signed version of std::size_t (C++23) |
| integral       | uz, uZ, Uz, UZ, zu, zU, Zu, ZU         | std::size_t (C++23)                       |
| floating point | f or F                                 | float                                     |
| floating point | l or L                                 | long double                               |
| string         | s                                      | std::string                               |
| string         | sv                                     | std::string_view                          |

s and sv are case sensitive literals

`"Hello, world!"` is a string literal. String literals are placed between double quotes to identify them as strings (as opposed to char literals, which are placed between single quotes).

This trailing ‘\0’ character is a special character called a **null terminator**, and it is used to indicate the end of the string. A string that ends with a null terminator is called a **null-terminated string**.

Unlike C-style string literals, `std::string` and `std::string_view` literals create temporary objects. These temporary objects must be used immediately, as they are destroyed at the end of the full expression in which they are created.


