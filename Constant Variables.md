#unit5

C++ supports two different kinds of constants:

- **Named constants** are constant values that are associated with an identifier. These are also sometimes called **symbolic constants**.
- **Literal constants** are constant values that are not associated with an identifier.

Const variables _must_ be initialized when you define them, and then that value can not be changed via assignment:

```cpp
const int constAge { age }; // initialize const variable using non-const value
```

**The initializer of a const variable can be a non-constant value.**

Prefer constant variables to preprocessor macros

A **type qualifier** (sometimes called a **qualifier** for short) is a keyword that is applied to a type that modifies how that type behaves. The `const` used to declare a constant variable is called a **const type qualifier** (or **const qualifier** for short).

