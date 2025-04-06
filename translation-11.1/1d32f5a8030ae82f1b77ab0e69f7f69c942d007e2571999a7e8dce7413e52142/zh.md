# Mathematical Operations and Elementary Functions

Julia 提供了一整套基本算术和按位运算符，适用于所有数值原始类型，并且提供了便携、高效的标准数学函数的全面实现。

## Arithmetic Operators

以下 [arithmetic operators](https://en.wikipedia.org/wiki/Arithmetic#Arithmetic_operations) 在所有原始数字类型上都受支持：

| Expression | Name           | Description                            |
|:---------- |:-------------- |:-------------------------------------- |
| `+x`       | unary plus     | the identity operation                 |
| `-x`       | unary minus    | maps values to their additive inverses |
| `x + y`    | binary plus    | performs addition                      |
| `x - y`    | binary minus   | performs subtraction                   |
| `x * y`    | times          | performs multiplication                |
| `x / y`    | divide         | performs division                      |
| `x ÷ y`    | integer divide | x / y, truncated to an integer         |
| `x \ y`    | inverse divide | equivalent to `y / x`                  |
| `x ^ y`    | power          | raises `x` to the `y`th power          |
| `x % y`    | remainder      | equivalent to `rem(x, y)`              |

一个数字字面量直接放在标识符或括号之前，例如 `2x` 或 `2(x + y)`，被视为乘法，优先级高于其他二元操作。有关详细信息，请参见 [Numeric Literal Coefficients](@ref man-numeric-literal-coefficients)。

Julia的提升系统使得对不同类型参数的混合进行算术运算“自然且自动地”工作。有关提升系统的详细信息，请参见 [Conversion and Promotion](@ref conversion-and-promotion)。

÷ 符号可以通过在 REPL 或 Julia IDE 中输入 `\div<tab>` 方便地输入。有关更多信息，请参见 [manual section on Unicode input](@ref Unicode-Input)。

这里有一些使用算术运算符的简单示例：

```jldoctest
julia> 1 + 2 + 3
6

julia> 1 - 2
-1

julia> 3*2/12
0.5
```

（根据惯例，如果运算符在其他附近运算符之前应用，我们倾向于将运算符的间距缩得更紧。例如，我们通常会写 `-x + 2` 来反映首先对 `x` 取负，然后将 `2` 加到该结果上。）

在乘法中，`false` 作为 *强零* 作用：

```jldoctest
julia> NaN * false
0.0

julia> false * Inf
0.0
```

这对于防止已知为零的数量中传播 `NaN` 值是有用的。请参见 [Knuth (1992)](https://arxiv.org/abs/math/9205211) 以获取动机。

## Boolean Operators

以下 [Boolean operators](https://en.wikipedia.org/wiki/Boolean_algebra#Operations) 在 [`Bool`](@ref) 类型上受支持：

| Expression | Name                                                    |
|:---------- |:------------------------------------------------------- |
| `!x`       | negation                                                |
| `x && y`   | [short-circuiting and](@ref man-conditional-evaluation) |
| `x \|\| y` | [short-circuiting or](@ref man-conditional-evaluation)  |

否定将 `true` 变为 `false`，反之亦然。短路操作在链接页面中进行了说明。

注意，`Bool` 是一种整数类型，所有通常的提升规则和数值运算符也适用于它。

## Bitwise Operators

以下 [bitwise operators](https://en.wikipedia.org/wiki/Bitwise_operation#Bitwise_operators) 在所有原始整数类型上都受支持：

| Expression | Name                                                                     |
|:---------- |:------------------------------------------------------------------------ |
| `~x`       | bitwise not                                                              |
| `x & y`    | bitwise and                                                              |
| `x \| y`   | bitwise or                                                               |
| `x ⊻ y`    | bitwise xor (exclusive or)                                               |
| `x ⊼ y`    | bitwise nand (not and)                                                   |
| `x ⊽ y`    | bitwise nor (not or)                                                     |
| `x >>> y`  | [logical shift](https://en.wikipedia.org/wiki/Logical_shift) right       |
| `x >> y`   | [arithmetic shift](https://en.wikipedia.org/wiki/Arithmetic_shift) right |
| `x << y`   | logical/arithmetic shift left                                            |

这里有一些位运算符的示例：

```jldoctest
julia> ~123
-124

julia> 123 & 234
106

julia> 123 | 234
251

julia> 123 ⊻ 234
145

julia> xor(123, 234)
145

julia> nand(123, 123)
-124

julia> 123 ⊼ 123
-124

julia> nor(123, 124)
-128

julia> 123 ⊽ 124
-128

julia> ~UInt32(123)
0xffffff84

julia> ~UInt8(123)
0x84
```

## Updating operators

每个二进制算术和按位运算符都有一个更新版本，它将操作的结果赋值回其左操作数。二进制运算符的更新版本是在运算符后面立即放置一个 `=`。例如，写 `x += 3` 等同于写 `x = x + 3`：

```jldoctest
julia> x = 1
1

julia> x += 3
4

julia> x
4
```

所有二进制算术和按位运算符的更新版本是：

```
+=  -=  *=  /=  \=  ÷=  %=  ^=  &=  |=  ⊻=  >>>=  >>=  <<=
```

!!! note
    一个更新操作符重新绑定左侧的变量。因此，变量的类型可能会改变。

    ```jldoctest
    julia> x = 0x01; typeof(x)
    UInt8

    julia> x *= 2 # Same as x = x * 2
    2

    julia> typeof(x)
    Int64
    ```


## [Vectorized "dot" operators](@id man-dot-operators)

对于 *每个* 二元运算符，如 `^`，都有一个对应的 "点" 运算符 `.^`，它 *自动* 定义为在数组上逐元素执行 `^`。例如，`[1, 2, 3] ^ 3` 是未定义的，因为对（非方形）数组进行 "立方" 没有标准的数学意义，但 `[1, 2, 3] .^ 3` 被定义为计算逐元素（或 "向量化"）的结果 `[1^3, 2^3, 3^3]`。 对于像 `!` 或 `√` 这样的单元运算符，同样有一个对应的 `.√`，它逐元素应用该运算符。

```jldoctest
julia> [1, 2, 3] .^ 3
3-element Vector{Int64}:
  1
  8
 27
```

更具体地说，`a .^ b` 被解析为 ["dot" call](@ref man-vectorized) `(^).(a,b)`，它执行一个 [broadcast](@ref Broadcasting) 操作：它可以组合数组和标量、相同大小的数组（逐元素执行操作），甚至不同形状的数组（例如，组合行向量和列向量以生成矩阵）。此外，像所有向量化的“点调用”一样，这些“点运算符”是*融合*的。例如，如果你计算 `2 .* A.^2 .+ sin.(A)`（或等效地使用 `@. 2A^2 + sin(A)`，使用 [`@.`](@ref @__dot__) 宏）对于数组 `A`，它会对 `A` 执行一个*单一*循环，为 `A` 的每个元素 `a` 计算 `2a^2 + sin(a)`。特别地，像 `f.(g.(x))` 这样的嵌套点调用是融合的，而“相邻”的二元运算符如 `x .+ 3 .* x.^2` 等价于嵌套点调用 `(+).(x, (*).(3, (^).(x, 2)))`。

Furthermore, "dotted" updating operators like `a .+= b` (or `@. a += b`) are parsed as `a .= a .+ b`, where `.=` is a fused *in-place* assignment operation (see the [dot syntax documentation](@ref man-vectorized)).

注意，点语法也适用于用户定义的运算符。例如，如果你定义 `⊗(A, B) = kron(A, B)` 来为 Kronecker 乘积提供一个方便的中缀语法 `A ⊗ B`（[`kron`](@ref)），那么 `[A, B] .⊗ [C, D]` 将计算 `[A⊗C, B⊗D]`，无需额外编码。

将点运算符与数字字面量结合可能会造成歧义。例如，`1.+x` 并不清楚是指 `1. + x` 还是 `1 .+ x`。因此，这种语法是不允许的，在这种情况下必须在运算符周围使用空格。

## Numeric Comparisons

标准比较操作适用于所有原始数值类型：

| Operator                     | Name                     |
|:---------------------------- |:------------------------ |
| [`==`](@ref)                 | equality                 |
| [`!=`](@ref), [`≠`](@ref !=) | inequality               |
| [`<`](@ref)                  | less than                |
| [`<=`](@ref), [`≤`](@ref <=) | less than or equal to    |
| [`>`](@ref)                  | greater than             |
| [`>=`](@ref), [`≥`](@ref >=) | greater than or equal to |

这里有一些简单的例子：

```jldoctest
julia> 1 == 1
true

julia> 1 == 2
false

julia> 1 != 2
true

julia> 1 == 1.0
true

julia> 1 < 2
true

julia> 1.0 > 3
false

julia> 1 >= 1.0
true

julia> -1 <= 1
true

julia> -1 <= -1
true

julia> -1 <= -2
false

julia> 3 < -0.5
false
```

整数以标准方式进行比较——通过比特比较。浮点数的比较依据 [IEEE 754 standard](https://en.wikipedia.org/wiki/IEEE_754-2008)：

  * 有限数以通常的方式排序。
  * 正零等于但不大于负零。
  * `Inf` 等于它自己，并且大于除了 `NaN` 以外的所有其他值。
  * `-Inf` 等于它自己，并且小于除了 `NaN` 以外的所有其他值。
  * `NaN` 不等于、也不小于、也不大于任何东西，包括它自己。

最后一点可能令人惊讶，因此值得注意：

```jldoctest
julia> NaN == NaN
false

julia> NaN != NaN
true

julia> NaN < NaN
false

julia> NaN > NaN
false
```

并且在处理 [arrays](@ref man-multi-dim-arrays) 时可能会导致头痛：

```jldoctest
julia> [1 NaN] == [1 NaN]
false
```

Julia 提供了额外的函数来测试数字的特殊值，这在哈希键比较等情况下非常有用：

| Function                | Tests if                  |
|:----------------------- |:------------------------- |
| [`isequal(x, y)`](@ref) | `x` and `y` are identical |
| [`isfinite(x)`](@ref)   | `x` is a finite number    |
| [`isinf(x)`](@ref)      | `x` is infinite           |
| [`isnan(x)`](@ref)      | `x` is not a number       |

[`isequal`](@ref) 将 `NaN` 视为彼此相等：

```jldoctest
julia> isequal(NaN, NaN)
true

julia> isequal([1 NaN], [1 NaN])
true

julia> isequal(NaN, NaN32)
true
```

`isequal` 还可以用来区分有符号零：

```jldoctest
julia> -0.0 == 0.0
true

julia> isequal(-0.0, 0.0)
false
```

混合类型的比较（有符号整数、无符号整数和浮点数之间）可能会很棘手。为了确保 Julia 正确地进行这些比较，已经进行了大量的工作。

对于其他类型，`isequal` 默认调用 [`==`](@ref)，因此如果您想为自己的类型定义相等性，则只需添加一个 `4d61726b646f776e2e436f64652822222c20223d3d2229_40726566` 方法。如果您定义了自己的相等性函数，您可能还应该定义一个相应的 [`hash`](@ref) 方法，以确保 `isequal(x,y)` 意味着 `hash(x) == hash(y)`。

### Chaining comparisons

与大多数语言不同，[notable exception of Python](https://en.wikipedia.org/wiki/Python_syntax_and_semantics#Comparison_operators)，比较可以任意链式连接：

```jldoctest
julia> 1 < 2 <= 2 < 3 == 3 > 2 >= 1 == 1 < 3 != 5
true
```

链式比较在数值代码中通常非常方便。链式比较使用 `&&` 运算符进行标量比较，而使用 [`&`](@ref) 运算符进行逐元素比较，这使得它们可以在数组上工作。例如，`0 .< A .< 1` 会生成一个布尔数组，其条目在 `A` 的相应元素介于 0 和 1 之间时为真。

注意链式比较的评估行为：

```jldoctest
julia> v(x) = (println(x); x)
v (generic function with 1 method)

julia> v(1) < v(2) <= v(3)
2
1
3
true

julia> v(1) > v(2) <= v(3)
2
1
false
```

中间的表达式只会被评估一次，而不是像将表达式写成 `v(1) < v(2) && v(2) <= v(3)` 时那样评估两次。然而，链式比较中的评估顺序是未定义的。强烈建议不要在链式比较中使用具有副作用的表达式（例如打印）。如果需要副作用，应显式使用短路 `&&` 运算符（参见 [Short-Circuit Evaluation](@ref)）。

### Elementary Functions

Julia 提供了一套全面的数学函数和运算符。这些数学运算被定义在尽可能广泛的数值类别上，以便进行合理的定义，包括整数、浮点数、有理数和复数，只要这些定义是合理的。

此外，这些函数（像任何Julia函数一样）可以以“向量化”的方式应用于数组和其他集合，使用 [dot syntax](@ref man-vectorized) `f.(A)`，例如 `sin.(A)` 将计算数组 `A` 中每个元素的正弦值。

## Operator Precedence and Associativity

朱莉亚按照以下运算的顺序和结合性进行操作，从最高优先级到最低优先级：

| Category       | Operators                                              | Associativity   |
|:-------------- |:------------------------------------------------------ |:--------------- |
| Syntax         | `.` followed by `::`                                   | Left            |
| Exponentiation | `^`                                                    | Right           |
| Unary          | `+ - ! ~ ¬ √ ∛ ∜ ⋆ ± ∓ <: >:`                          | Right[^1]       |
| Bitshifts      | `<< >> >>>`                                            | Left            |
| Fractions      | `//`                                                   | Left            |
| Multiplication | `* / % & \ ÷`                                          | Left[^2]        |
| Addition       | `+ - \| ⊻`                                             | Left[^2]        |
| Syntax         | `: ..`                                                 | Left            |
| Syntax         | `\|>`                                                  | Left            |
| Syntax         | `<\|`                                                  | Right           |
| Comparisons    | `> < >= <= == === != !== <:`                           | Non-associative |
| Control flow   | `&&` followed by `\|\|` followed by `?`                | Right           |
| Pair           | `=>`                                                   | Right           |
| Assignments    | `= += -= *= /= //= \= ^= ÷= %= \|= &= ⊻= <<= >>= >>>=` | Right           |

[^1]: The unary operators `+` and `-` require explicit parentheses around their argument to disambiguate them from the operator `++`, etc. Other compositions of unary operators are parsed with right-associativity, e. g., `√√-a` as `√(√(-a))`.

[^2]: The operators `+`, `++` and `*` are non-associative. `a + b + c` is parsed as `+(a, b, c)` not `+(+(a, b), c)`. However, the fallback methods for `+(a, b, c, d...)` and `*(a, b, c, d...)` both default to left-associative evaluation.

有关 *每个* Julia 运算符优先级的完整列表，请参见此文件的顶部： [`src/julia-parser.scm`](https://github.com/JuliaLang/julia/blob/master/src/julia-parser.scm)。请注意，那里的一些运算符在 `Base` 模块中未定义，但可能会由标准库、包或用户代码提供定义。

您还可以通过内置函数 `Base.operator_precedence` 查找任何给定运算符的数值优先级，其中较高的数字具有优先权：

```jldoctest
julia> Base.operator_precedence(:+), Base.operator_precedence(:*), Base.operator_precedence(:.)
(11, 12, 17)

julia> Base.operator_precedence(:sin), Base.operator_precedence(:+=), Base.operator_precedence(:(=))  # (Note the necessary parens on `:(=)`)
(0, 1, 1)
```

一个表示运算符结合性的符号也可以通过调用内置函数 `Base.operator_associativity` 来找到：

```jldoctest
julia> Base.operator_associativity(:-), Base.operator_associativity(:+), Base.operator_associativity(:^)
(:left, :none, :right)

julia> Base.operator_associativity(:⊗), Base.operator_associativity(:sin), Base.operator_associativity(:→)
(:left, :none, :right)
```

请注意，像 `:sin` 这样的符号返回优先级 `0`。这个值表示无效的运算符，而不是最低优先级的运算符。同样，这些运算符被分配了结合性 `:none`。

[Numeric literal coefficients](@ref man-numeric-literal-coefficients)，例如 `2x`，被视为乘法，其优先级高于任何其他二元运算，除了 `^`，在作为指数时它们的优先级更高。

```jldoctest
julia> x = 3; 2x^2
18

julia> x = 3; 2^2x
64
```

并列解析起来像一个一元运算符，它在指数周围具有相同的自然不对称性：`-x^y` 和 `2x^y` 解析为 `-(x^y)` 和 `2(x^y)`，而 `x^-y` 和 `x^2y` 解析为 `x^(-y)` 和 `x^(2y)`。

## Numerical Conversions

Julia 支持三种数值转换形式，它们在处理不精确转换时有所不同。

  * 符号 `T(x)` 或 `convert(T, x)` 将 `x` 转换为类型 `T` 的值。

      * 如果 `T` 是浮点类型，则结果是最接近的可表示值，这可能是正无穷大或负无穷大。
      * 如果 `T` 是整数类型，当 `x` 不能被 `T` 表示时，将引发 `InexactError`。
  * `x % T` 将整数 `x` 转换为与 `x` 模 `2^n` 同余的整数类型 `T` 的值，其中 `n` 是 `T` 中的位数。换句话说，二进制表示被截断以适应。
  * [Rounding functions](@ref) 将类型 `T` 作为可选参数。例如，`round(Int,x)` 是 `Int(round(x))` 的简写。

以下示例展示了不同的形式。

```jldoctest
julia> Int8(127)
127

julia> Int8(128)
ERROR: InexactError: trunc(Int8, 128)
Stacktrace:
[...]

julia> Int8(127.0)
127

julia> Int8(3.14)
ERROR: InexactError: Int8(3.14)
Stacktrace:
[...]

julia> Int8(128.0)
ERROR: InexactError: Int8(128.0)
Stacktrace:
[...]

julia> 127 % Int8
127

julia> 128 % Int8
-128

julia> round(Int8,127.4)
127

julia> round(Int8,127.6)
ERROR: InexactError: Int8(128.0)
Stacktrace:
[...]
```

查看 [Conversion and Promotion](@ref conversion-and-promotion) 以了解如何定义您自己的转换和促销。

### Rounding functions

| Function              | Description                      | Return type |
|:--------------------- |:-------------------------------- |:----------- |
| [`round(x)`](@ref)    | round `x` to the nearest integer | `typeof(x)` |
| [`round(T, x)`](@ref) | round `x` to the nearest integer | `T`         |
| [`floor(x)`](@ref)    | round `x` towards `-Inf`         | `typeof(x)` |
| [`floor(T, x)`](@ref) | round `x` towards `-Inf`         | `T`         |
| [`ceil(x)`](@ref)     | round `x` towards `+Inf`         | `typeof(x)` |
| [`ceil(T, x)`](@ref)  | round `x` towards `+Inf`         | `T`         |
| [`trunc(x)`](@ref)    | round `x` towards zero           | `typeof(x)` |
| [`trunc(T, x)`](@ref) | round `x` towards zero           | `T`         |

### Division functions

| Function                   | Description                                                                                               |
|:-------------------------- |:--------------------------------------------------------------------------------------------------------- |
| [`div(x, y)`](@ref), `x÷y` | truncated division; quotient rounded towards zero                                                         |
| [`fld(x, y)`](@ref)        | floored division; quotient rounded towards `-Inf`                                                         |
| [`cld(x, y)`](@ref)        | ceiling division; quotient rounded towards `+Inf`                                                         |
| [`rem(x, y)`](@ref), `x%y` | remainder; satisfies `x == div(x, y)*y + rem(x, y)`; sign matches `x`                                     |
| [`mod(x, y)`](@ref)        | modulus; satisfies `x == fld(x, y)*y + mod(x, y)`; sign matches `y`                                       |
| [`mod1(x, y)`](@ref)       | `mod` with offset 1; returns `r∈(0, y]` for `y>0` or `r∈[y, 0)` for `y<0`, where `mod(r, y) == mod(x, y)` |
| [`mod2pi(x)`](@ref)        | modulus with respect to 2pi;  `0 <= mod2pi(x) < 2pi`                                                      |
| [`divrem(x, y)`](@ref)     | returns `(div(x, y),rem(x, y))`                                                                           |
| [`fldmod(x, y)`](@ref)     | returns `(fld(x, y), mod(x, y))`                                                                          |
| [`gcd(x, y...)`](@ref)     | greatest positive common divisor of `x`, `y`,...                                                          |
| [`lcm(x, y...)`](@ref)     | least positive common multiple of `x`, `y`,...                                                            |

### Sign and absolute value functions

| Function                 | Description                                                |
|:------------------------ |:---------------------------------------------------------- |
| [`abs(x)`](@ref)         | a positive value with the magnitude of `x`                 |
| [`abs2(x)`](@ref)        | the squared magnitude of `x`                               |
| [`sign(x)`](@ref)        | indicates the sign of `x`, returning -1, 0, or +1          |
| [`signbit(x)`](@ref)     | indicates whether the sign bit is on (true) or off (false) |
| [`copysign(x, y)`](@ref) | a value with the magnitude of `x` and the sign of `y`      |
| [`flipsign(x, y)`](@ref) | a value with the magnitude of `x` and the sign of `x*y`    |

### Powers, logs and roots

| Function                 | Description                                                                |
|:------------------------ |:-------------------------------------------------------------------------- |
| [`sqrt(x)`](@ref), `√x`  | square root of `x`                                                         |
| [`cbrt(x)`](@ref), `∛x`  | cube root of `x`                                                           |
| [`hypot(x, y)`](@ref)    | hypotenuse of right-angled triangle with other sides of length `x` and `y` |
| [`exp(x)`](@ref)         | natural exponential function at `x`                                        |
| [`expm1(x)`](@ref)       | accurate `exp(x) - 1` for `x` near zero                                    |
| [`ldexp(x, n)`](@ref)    | `x * 2^n` computed efficiently for integer values of `n`                   |
| [`log(x)`](@ref)         | natural logarithm of `x`                                                   |
| [`log(b, x)`](@ref)      | base `b` logarithm of `x`                                                  |
| [`log2(x)`](@ref)        | base 2 logarithm of `x`                                                    |
| [`log10(x)`](@ref)       | base 10 logarithm of `x`                                                   |
| [`log1p(x)`](@ref)       | accurate `log(1 + x)` for `x` near zero                                    |
| [`exponent(x)`](@ref)    | binary exponent of `x`                                                     |
| [`significand(x)`](@ref) | binary significand (a.k.a. mantissa) of a floating-point number `x`        |

有关为什么像 [`hypot`](@ref)、[`expm1`](@ref) 和 [`log1p`](@ref) 这样的函数是必要和有用的概述，请参阅 John D. Cook 关于该主题的优秀博客文章对：[expm1, log1p, erfc](https://www.johndcook.com/blog/2010/06/07/math-library-functions-that-seem-unnecessary/) 和 [hypot](https://www.johndcook.com/blog/2010/06/02/whats-so-hard-about-finding-a-hypotenuse/)。

### Trigonometric and hyperbolic functions

所有标准的三角函数和双曲函数也被定义为：

```
sin    cos    tan    cot    sec    csc
sinh   cosh   tanh   coth   sech   csch
asin   acos   atan   acot   asec   acsc
asinh  acosh  atanh  acoth  asech  acsch
sinc   cosc
```

这些都是单参数函数，[`atan`](@ref) 还接受两个参数，对应于传统的 [`atan2`](https://en.wikipedia.org/wiki/Atan2) 函数。

此外，[`sinpi(x)`](@ref) 和 [`cospi(x)`](@ref) 被提供用于更准确地计算 [`sin(pi * x)`](@ref) 和 [`cos(pi * x)`](@ref)。

为了使用度数而不是弧度计算三角函数，请在函数后加上 `d`。例如，[`sind(x)`](@ref) 计算 `x` 的正弦，其中 `x` 以度数表示。带有度数变体的三角函数完整列表是：

```
sind   cosd   tand   cotd   secd   cscd
asind  acosd  atand  acotd  asecd  acscd
```

### Special functions

许多其他特殊数学函数由包 [SpecialFunctions.jl](https://github.com/JuliaMath/SpecialFunctions.jl) 提供。
