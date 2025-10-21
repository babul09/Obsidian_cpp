#unit4
n this case, if `u` was signed, the correct result would be produced. But because `u` is unsigned (which is easy to miss), `s` gets converted to unsigned, and the result (`-1`) is treated as an unsigned value. Since `-1` can’t be stored in an unsigned value, so we get overflow and an unexpected answer.

Here’s another example where things go wrong:

```cpp
#include <iostream>

// assume int is 4 bytes
int main()
{
    signed int s { -1 };
    unsigned int u { 1 };

    if (s < u) // -1 is implicitly converted to 4294967295, and 4294967295 < 1 is false
        std::cout << "-1 is less than 1\n";
    else
        std::cout << "1 is less than -1\n"; // this statement executes

    return 0;
}
```

There are still a few cases in C++ where it’s okay / necessary to use unsigned numbers.

First, unsigned numbers are preferred when dealing with bit manipulation (covered in chapter O -- that’s a capital ‘o’, not a ‘0’). They are also useful when well-defined wrap-around behavior is required (useful in some algorithms like encryption and random number generation).

Second, use of unsigned numbers is still unavoidable in some cases, mainly those having to do with array indexing. We’ll talk more about this in the lessons on arrays and array indexing.

Also note that if you’re developing for an embedded system (e.g. an Arduino) or some other processor/memory limited context, use of unsigned numbers is more common and accepted (and in some cases, unavoidable) for performance reasons.

[[Fixed Witdh Integers and size_t]]