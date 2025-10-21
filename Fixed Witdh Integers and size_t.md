#unit4


To address the above issues, C++11 provides an alternate set of integer types that are guaranteed to be the same size on any architecture. Because the size of these integers is fixed, they are called **fixed-width integers**.

|               |                 |                                                         |                                                                |
| ------------- | --------------- | ------------------------------------------------------- | -------------------------------------------------------------- |
| std::int8_t   | 1 byte signed   | -128 to 127                                             | Treated like a signed char on many systems. See note below.    |
| std::uint8_t  | 1 byte unsigned | 0 to 255                                                | Treated like an unsigned char on many systems. See note below. |
| std::int16_t  | 2 byte signed   | -32,768 to 32,767                                       |                                                                |
| std::uint16_t | 2 byte unsigned | 0 to 65,535                                             |                                                                |
| std::int32_t  | 4 byte signed   | -2,147,483,648 to 2,147,483,647                         |                                                                |
| std::uint32_t | 4 byte unsigned | 0 to 4,294,967,295                                      |                                                                |
| std::int64_t  | 8 byte signed   | -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807 |                                                                |
| std::uint64_t | 8 byte unsigned | 0 to 18,446,744,073,709,551,615                         |                                                                |
|               |                 |                                                         |                                                                |
==(in the <cstdint>\ header)==

The fixed-width integers actually don’t define new types -- they are just aliases for existing integral types with the desired size. For each fixed-width type, the implementation (the compiler and standard library) gets to determine which existing type is aliased. As an example, on a platform where `int` is 32-bits, `std::int32_t` will be an alias for `int`. On a system where `int` is 16-bits (and `long` is 32-bits), `std::int32_t` will be an alias for `long` instead.

So what about the 8-bit fixed-width types?

In most cases, `std::int8_t` is an alias for `signed char` because it is the only available 8-bit signed integral type (`bool` and `char` are not considered to be signed integral types). And when this is the case, `std::int8_t` will behave just like a char on that platform.

==To help address the above downsides, C++ also defines two alternative sets of integers that are guaranteed to exist.==

The fast types (std::int_fast#_t and std::uint_fast#_t) provide the fastest signed/unsigned integer type with a width of at least # bits (where # = 8, 16, 32, or 64). For example, `std::int_fast32_t` will give you the fastest signed integer type that’s at least 32-bits. By fastest, we mean the integral type that can be processed most quickly by the CPU.

The least types (std::int_least#_t and std::uint_least#_t) provide the smallest signed/unsigned integer type with a width of at least # bits (where # = 8, 16, 32, or 64). For example, `std::uint_least32_t` will give you the smallest unsigned integer type that’s at least 32-bits.


Best practice

- Prefer `int` when the size of the integer doesn’t matter (e.g. the number will always fit within the range of a 2-byte signed integer). For example, if you’re asking the user to enter their age, or counting from 1 to 10, it doesn’t matter whether `int` is 16-bits or 32-bits (the numbers will fit either way). This will cover the vast majority of the cases you’re likely to run across.
- Prefer `std::int#_t` when storing a quantity that needs a guaranteed range.
- Prefer `std::uint#_t` when doing bit manipulation or well-defined wrap-around behavior is required (e.g. for cryptography or random number generation).

Avoid the following when possible:

- `short` and `long` integers (prefer a fixed-width integer type instead).
- The fast and least integral types (prefer a fixed-width integer type instead).
- Unsigned types for holding quantities (prefer a signed integer type instead).
- The 8-bit fixed-width integer types (prefer a 16-bit fixed-width integer type instead).
- Any compiler-specific fixed-width integers (for example, Visual Studio defines __int8, __int16, etc…)

`std::size_t` is an alias for an implementation-defined unsigned integral type. It is used within the standard library to represent the byte-size or length of objects.
[[Floating point types]]
