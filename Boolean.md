#unit4 

bool initialises default to false
booleans are considered to be integral type

Use `std::boolalpha` to print `true` or `false`

If you want `std::cout` to print `true` or `false` instead of `0` or `1`, you can output `std::boolalpha`. This doesn’t output anything, but manipulates the way `std::cout` outputs `bool` values.

Here’s an example:

```cpp
#include <iostream>

int main()
{
    std::cout << true << '\n';
    std::cout << false << '\n';

    std::cout << std::boolalpha; // print bools as true or false

    std::cout << true << '\n';
    std::cout << false << '\n';
    return 0;
}
```

You can use `std::noboolalpha` to turn it back off.


However, in any context where an integer can be converted to a Boolean, the integer `0` is converted to `false`, and any other integer is converted to `true`.

```cpp
#include <iostream>

int main()
{
	std::cout << std::boolalpha; // print bools as true or false

	bool b1 = 4 ; // copy initialization allows implicit conversion from int to bool
	std::cout << b1 << '\n';

	bool b2 = 0 ; // copy initialization allows implicit conversion from int to bool
	std::cout << b2 << '\n';

	return 0;
}
```

To allow `std::cin` to accept the words `false` and `true` as inputs, you must first input to `std::boolalpha`:

```cpp
#include <iostream>

int main()
{
	bool b{};
	std::cout << "Enter a boolean value: ";

	// Allow the user to input 'true' or 'false' for boolean values
	// This is case-sensitive, so True or TRUE will not work
	std::cin >> std::boolalpha;
	std::cin >> b;
```

[[last topics 4]]