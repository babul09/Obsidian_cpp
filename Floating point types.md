#unit4

| Category       | C++ Type    | Typical Size       |
| -------------- | ----------- | ------------------ |
| floating point | float       | 4 bytes            |
|                | double      | 8 bytes            |
|                | long double | 8, 12, or 16 bytes |

```cpp
double b { 5.0 }; // 5.0 is a floating point literal (no suffix means double type by default)
float c { 5.0f }; // 5.0 is a floating point literal, f suffix means float type
```

cout has a default precision of 6 significant digits;

We can override the default precision that std::cout shows by using an `output manipulator` function named `std::setprecision()`. **Output manipulators** alter how data is output, and are defined in the _iomanip_ header.

```cpp
#include <iomanip> // for output manipulator std::setprecision()
#include <iostream>

int main()
{
    std::cout << std::setprecision(17); // show 17 digits of precision
    std::cout << 3.33333333333333333333333333333333333333f <<'\n'; // f suffix means float
    std::cout << 3.33333333333333333333333333333333333333 << '\n'; // no suffix means double

    return 0;
}
```

Outputs:

3.3333332538604736
3.3333333333333335


output manipulator **setw** is resets after every use and must be re-set for every instance;

Best practice is to use double over float as not doing so will cause lack of precision;

<iomanip> header used for the manipulator std::setprecision;

rounding numbers always and regularly produce error.
always assume your floating point nos are not precise.

NaN and Inf

IEEE 754 compatible formats additionally support some special values:

- **Inf**, which represents infinity. Inf is signed, and can be positive (+Inf) or negative (-Inf).
- **NaN**, which stands for “Not a Number”. There are several different kinds of NaN (which we won’t discuss here).
- Signed zero, meaning there are separate representations for “positive zero” (+0.0) and “negative zero” (-0.0).

Formats that are not compatible with IEEE 754 may not support some (or any) of these values. In such cases, code that uses or generates these special values will produce implementation-defined behavior.

[[Boolean]]