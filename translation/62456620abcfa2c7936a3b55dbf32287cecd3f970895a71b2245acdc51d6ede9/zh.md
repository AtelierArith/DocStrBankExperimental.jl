# Integers and Floating-Point Numbers

整数和浮点值是算术和计算的基本构建块。这些值的内置表示称为数值原始类型，而整数和浮点数在代码中作为立即值的表示被称为数值字面量。例如，`1` 是一个整数字面量，而 `1.0` 是一个浮点字面量；它们在内存中的二进制表示作为对象是数值原始类型。

Julia 提供了广泛的原始数值类型，并且定义了一整套算术和位运算符以及标准数学函数。这些直接映射到现代计算机本地支持的数值类型和操作，从而使 Julia 能够充分利用计算资源。此外，Julia 还提供了对 [Arbitrary Precision Arithmetic](@ref) 的软件支持，可以处理在本地硬件表示中无法有效表示的数值操作，但代价是相对较慢的性能。

以下是Julia的基本数值类型：

  * **整数类型：**

| Type              | Signed? | Number of bits | Smallest value | Largest value |
|:----------------- |:------- |:-------------- |:-------------- |:------------- |
| [`Int8`](@ref)    | ✓       | 8              | -2^7           | 2^7 - 1       |
| [`UInt8`](@ref)   |         | 8              | 0              | 2^8 - 1       |
| [`Int16`](@ref)   | ✓       | 16             | -2^15          | 2^15 - 1      |
| [`UInt16`](@ref)  |         | 16             | 0              | 2^16 - 1      |
| [`Int32`](@ref)   | ✓       | 32             | -2^31          | 2^31 - 1      |
| [`UInt32`](@ref)  |         | 32             | 0              | 2^32 - 1      |
| [`Int64`](@ref)   | ✓       | 64             | -2^63          | 2^63 - 1      |
| [`UInt64`](@ref)  |         | 64             | 0              | 2^64 - 1      |
| [`Int128`](@ref)  | ✓       | 128            | -2^127         | 2^127 - 1     |
| [`UInt128`](@ref) |         | 128            | 0              | 2^128 - 1     |
| [`Bool`](@ref)    | N/A     | 8              | `false` (0)    | `true` (1)    |

  * **浮点类型：**

| Type              | Precision                                                                      | Number of bits |
|:----------------- |:------------------------------------------------------------------------------ |:-------------- |
| [`Float16`](@ref) | [half](https://en.wikipedia.org/wiki/Half-precision_floating-point_format)     | 16             |
| [`Float32`](@ref) | [single](https://en.wikipedia.org/wiki/Single_precision_floating-point_format) | 32             |
| [`Float64`](@ref) | [double](https://en.wikipedia.org/wiki/Double_precision_floating-point_format) | 64             |

此外，[Complex and Rational Numbers](@ref) 的全面支持建立在这些原始数值类型之上。所有数值类型自然地相互操作，无需显式转换，这得益于灵活的、用户可扩展的 [type promotion system](@ref conversion-and-promotion)。

## Integers

字面整数以标准方式表示：

```jldoctest
julia> 1
1

julia> 1234
1234
```

整数字面量的默认类型取决于目标系统是 32 位架构还是 64 位架构：

```julia-repl
# 32-bit system:
julia> typeof(1)
Int32

# 64-bit system:
julia> typeof(1)
Int64
```

Julia内部变量 [`Sys.WORD_SIZE`](@ref) 表示目标系统是32位还是64位：

```julia-repl
# 32-bit system:
julia> Sys.WORD_SIZE
32

# 64-bit system:
julia> Sys.WORD_SIZE
64
```

Julia 还定义了类型 `Int` 和 `UInt`，它们分别是系统的有符号和无符号原生整数类型的别名：

```julia-repl
# 32-bit system:
julia> Int
Int32
julia> UInt
UInt32

# 64-bit system:
julia> Int
Int64
julia> UInt
UInt64
```

无法仅使用32位表示但可以在64位中表示的较大整数字面量始终会创建64位整数，无论系统类型如何：

```jldoctest
# 32-bit or 64-bit system:
julia> typeof(3000000000)
Int64
```

无符号整数的输入和输出使用 `0x` 前缀和十六进制（基数 16）数字 `0-9a-f`（大写数字 `A-F` 也可以用于输入）。无符号值的大小由使用的十六进制数字的数量决定：

```jldoctest
julia> x = 0x1
0x01

julia> typeof(x)
UInt8

julia> x = 0x123
0x0123

julia> typeof(x)
UInt16

julia> x = 0x1234567
0x01234567

julia> typeof(x)
UInt32

julia> x = 0x123456789abcdef
0x0123456789abcdef

julia> typeof(x)
UInt64

julia> x = 0x11112222333344445555666677778888
0x11112222333344445555666677778888

julia> typeof(x)
UInt128
```

这种行为基于这样的观察：当使用无符号十六进制字面量表示整数值时，通常是为了表示一个固定的数字字节序列，而不仅仅是一个整数值。

二进制和八进制字面量也受到支持：

```jldoctest
julia> x = 0b10
0x02

julia> typeof(x)
UInt8

julia> x = 0o010
0x08

julia> typeof(x)
UInt8

julia> x = 0x00000000000000001111222233334444
0x00000000000000001111222233334444

julia> typeof(x)
UInt128
```

对于十六进制字面量，二进制和八进制字面量产生无符号整数类型。二进制数据项的大小是所需的最小大小，如果字面量的首位数字不是 `0`。在首位为零的情况下，大小由具有相同长度但首位数字为 `1` 的字面量所需的最小大小决定。这意味着：

  * `0x1` 和 `0x12` 是 `UInt8` 字面量，
  * `0x123` 和 `0x1234` 是 `UInt16` 字面量，
  * `0x12345` 和 `0x12345678` 是 `UInt32` 字面量，
  * `0x123456789` 和 `0x1234567890adcdef` 是 `UInt64` 字面量，等等。

即使存在不影响数值的前导零数字，它们也会计入字面量的存储大小。因此，`0x01` 是 `UInt8`，而 `0x0001` 是 `UInt16`。

这允许用户控制大小。

无符号字面量（以 `0x` 开头）编码的整数如果太大而无法表示为 `UInt128` 值，将构造 `BigInt` 值。虽然这不是一种无符号类型，但它是唯一足够大的内置类型，可以表示如此大的整数值。

二进制、八进制和十六进制字面量可以通过在无符号字面量前面立即加上 `-` 来表示为负数。它们产生的无符号整数与无符号字面量的大小相同，值为其二的补数：

```jldoctest
julia> -0x2
0xfe

julia> -0x0002
0xfffe
```

原始数值类型（如整数）的最小和最大可表示值由 [`typemin`](@ref) 和 [`typemax`](@ref) 函数给出：

```jldoctest
julia> (typemin(Int32), typemax(Int32))
(-2147483648, 2147483647)

julia> for T in [Int8,Int16,Int32,Int64,Int128,UInt8,UInt16,UInt32,UInt64,UInt128]
           println("$(lpad(T,7)): [$(typemin(T)),$(typemax(T))]")
       end
   Int8: [-128,127]
  Int16: [-32768,32767]
  Int32: [-2147483648,2147483647]
  Int64: [-9223372036854775808,9223372036854775807]
 Int128: [-170141183460469231731687303715884105728,170141183460469231731687303715884105727]
  UInt8: [0,255]
 UInt16: [0,65535]
 UInt32: [0,4294967295]
 UInt64: [0,18446744073709551615]
UInt128: [0,340282366920938463463374607431768211455]
```

[`typemin`](@ref) 和 [`typemax`](@ref) 返回的值始终是给定参数类型的。（上述表达式使用了几种尚未引入的特性，包括 [for loops](@ref man-loops)、[Strings](@ref man-strings) 和 [Interpolation](@ref string-interpolation)，但对于一些已有编程经验的用户来说应该足够容易理解。）

### Overflow behavior

在Julia中，超过给定类型的最大可表示值会导致环绕行为：

```jldoctest
julia> x = typemax(Int64)
9223372036854775807

julia> x + 1
-9223372036854775808

julia> x + 1 == typemin(Int64)
true
```

算术运算与 Julia 的整数类型本质上执行 [modular arithmetic](https://en.wikipedia.org/wiki/Modular_arithmetic)，反映了现代计算机硬件上整数运算的特性。在溢出可能发生的情况下，明确检查可能由此类溢出引起的环绕效应至关重要。[`Base.Checked`](@ref) 模块提供了一套配备溢出检查的算术运算，如果发生溢出则会触发错误。对于在任何情况下都无法容忍溢出的用例，建议使用 [`BigInt`](@ref) 类型，如 [Arbitrary Precision Arithmetic](@ref) 中详细说明的那样。

溢出行为的一个示例及其潜在解决方案如下：

```jldoctest
julia> 10^19
-8446744073709551616

julia> big(10)^19
10000000000000000000
```

### Division errors

整数除法（`div` 函数）有两个特殊情况：除以零，以及将最低负数 ([`typemin`](@ref)) 除以 -1。这两种情况都会抛出一个 [`DivideError`](@ref)。当余数和模数函数（`rem` 和 `mod`）的第二个参数为零时，也会抛出一个 `4d61726b646f776e2e436f64652822222c20224469766964654572726f722229_40726566`。

## Floating-Point Numbers

字面浮点数以标准格式表示，使用 [E-notation](https://en.wikipedia.org/wiki/Scientific_notation#E_notation) 在必要时：

```jldoctest
julia> 1.0
1.0

julia> 1.
1.0

julia> 0.5
0.5

julia> .5
0.5

julia> -1.23
-1.23

julia> 1e10
1.0e10

julia> 2.5e-4
0.00025
```

上述结果都是 [`Float64`](@ref) 值。字面上的 [`Float32`](@ref) 值可以通过在 `e` 的位置写一个 `f` 来输入：

```jldoctest
julia> x = 0.5f0
0.5f0

julia> typeof(x)
Float32

julia> 2.5f-4
0.00025f0
```

值可以轻松转换为 [`Float32`](@ref)：

```jldoctest
julia> x = Float32(-1.5)
-1.5f0

julia> typeof(x)
Float32
```

十六进制浮点字面量也是有效的，但仅作为 [`Float64`](@ref) 值，前面带有 `p` 的二进制指数：

```jldoctest
julia> 0x1p0
1.0

julia> 0x1.8p3
12.0

julia> x = 0x.4p-1
0.125

julia> typeof(x)
Float64
```

半精度浮点数也被支持（[`Float16`](@ref)），但它们是通过软件实现的，并使用 [`Float32`](@ref) 进行计算。

```jldoctest
julia> sizeof(Float16(4.))
2

julia> 2*Float16(4.)
Float16(8.0)
```

下划线 `_` 可以用作数字分隔符：

```jldoctest
julia> 10_000, 0.000_000_005, 0xdead_beef, 0b1011_0010
(10000, 5.0e-9, 0xdeadbeef, 0xb2)
```

### Floating-point zero

浮点数有 [two zeros](https://en.wikipedia.org/wiki/Signed_zero)，正零和负零。它们彼此相等，但具有不同的二进制表示，可以使用 [`bitstring`](@ref) 函数看到这一点：

```jldoctest
julia> 0.0 == -0.0
true

julia> bitstring(0.0)
"0000000000000000000000000000000000000000000000000000000000000000"

julia> bitstring(-0.0)
"1000000000000000000000000000000000000000000000000000000000000000"
```

### Special floating-point values

有三个指定的标准浮点值，它们不对应于实数线上的任何点：

| `Float16` | `Float32` | `Float64` | Name              | Description                                                     |
|:--------- |:--------- |:--------- |:----------------- |:--------------------------------------------------------------- |
| `Inf16`   | `Inf32`   | `Inf`     | positive infinity | a value greater than all finite floating-point values           |
| `-Inf16`  | `-Inf32`  | `-Inf`    | negative infinity | a value less than all finite floating-point values              |
| `NaN16`   | `NaN32`   | `NaN`     | not a number      | a value not `==` to any floating-point value (including itself) |

有关这些非有限浮点值如何相互排序以及与其他浮点值的关系的进一步讨论，请参见 [Numeric Comparisons](@ref)。根据 [IEEE 754 standard](https://en.wikipedia.org/wiki/IEEE_754-2008)，这些浮点值是某些算术运算的结果：

```jldoctest
julia> 1/Inf
0.0

julia> 1/0
Inf

julia> -5/0
-Inf

julia> 0.000001/0
Inf

julia> 0/0
NaN

julia> 500 + Inf
Inf

julia> 500 - Inf
-Inf

julia> Inf + Inf
Inf

julia> Inf - Inf
NaN

julia> Inf * Inf
Inf

julia> Inf / Inf
NaN

julia> 0 * Inf
NaN

julia> NaN == NaN
false

julia> NaN != NaN
true

julia> NaN < NaN
false

julia> NaN > NaN
false
```

[`typemin`](@ref) 和 [`typemax`](@ref) 函数也适用于浮点类型：

```jldoctest
julia> (typemin(Float16),typemax(Float16))
(-Inf16, Inf16)

julia> (typemin(Float32),typemax(Float32))
(-Inf32, Inf32)

julia> (typemin(Float64),typemax(Float64))
(-Inf, Inf)
```

### Machine epsilon

大多数实数无法用浮点数精确表示，因此在许多情况下，了解两个相邻可表示浮点数之间的距离是很重要的，这通常被称为 [machine epsilon](https://en.wikipedia.org/wiki/Machine_epsilon)。

Julia 提供了 [`eps`](@ref)，这给出了 `1.0` 和下一个可表示的浮点值之间的距离：

```jldoctest
julia> eps(Float32)
1.1920929f-7

julia> eps(Float64)
2.220446049250313e-16

julia> eps() # same as eps(Float64)
2.220446049250313e-16
```

这些值分别是 `2.0^-23` 和 `2.0^-52`，对应的值为 [`Float32`](@ref) 和 [`Float64`](@ref)。[`eps`](@ref) 函数也可以接受一个浮点值作为参数，并给出该值与下一个可表示的浮点值之间的绝对差。也就是说，`eps(x)` 产生一个与 `x` 相同类型的值，使得 `x + eps(x)` 是比 `x` 大的下一个可表示的浮点值：

```jldoctest
julia> eps(1.0)
2.220446049250313e-16

julia> eps(1000.)
1.1368683772161603e-13

julia> eps(1e-27)
1.793662034335766e-43

julia> eps(0.0)
5.0e-324
```

两个相邻可表示浮点数之间的距离不是恒定的，而是对于较小的值较小，对于较大的值较大。换句话说，可表示的浮点数在实数线上在零附近最为密集，随着远离零的距离增加而呈指数级稀疏。根据定义，`eps(1.0)` 与 `eps(Float64)` 是相同的，因为 `1.0` 是一个 64 位浮点值。

Julia 还提供了 [`nextfloat`](@ref) 和 [`prevfloat`](@ref) 函数，分别返回可表示的下一个更大或更小的浮点数。

```jldoctest
julia> x = 1.25f0
1.25f0

julia> nextfloat(x)
1.2500001f0

julia> prevfloat(x)
1.2499999f0

julia> bitstring(prevfloat(x))
"00111111100111111111111111111111"

julia> bitstring(x)
"00111111101000000000000000000000"

julia> bitstring(nextfloat(x))
"00111111101000000000000000000001"
```

这个例子突出了一个一般原则，即相邻的可表示浮点数也具有相邻的二进制整数表示。

### Rounding modes

如果一个数字没有精确的浮点表示，它必须被四舍五入到一个合适的可表示值。然而，如果需要，可以根据在 [IEEE 754 standard](https://en.wikipedia.org/wiki/IEEE_754-2008) 中提出的舍入模式来改变这种舍入方式。

默认使用的模式始终是 [`RoundNearest`](@ref)，它会四舍五入到最接近的可表示值，平局时向最近的具有偶数最低有效位的值四舍五入。

### Background and References

浮点运算包含许多微妙之处，这对不熟悉底层实现细节的用户来说可能会令人惊讶。然而，这些微妙之处在大多数科学计算书籍中都有详细描述，并且在以下参考文献中也有说明：

  * 浮点算术的权威指南是 [IEEE 754-2008 Standard](https://standards.ieee.org/standard/754-2008.html)；然而，它并不在网上免费提供。
  * 有关浮点数如何表示的简要而清晰的介绍，请参见 John D. Cook 的 [article](https://www.johndcook.com/blog/2009/04/06/anatomy-of-a-floating-point-number/) 以及他关于如何这种表示在行为上与理想化的实数抽象不同所引发的一些问题的 [introduction](https://www.johndcook.com/blog/2009/04/06/numbers-are-a-leaky-abstraction/)。
  * 也推荐布鲁斯·道森的 [series of blog posts on floating-point numbers](https://randomascii.wordpress.com/2012/05/20/thats-not-normalthe-performance-of-odd-floats/)。
  * 有关浮点数及其计算时遇到的数值精度问题的优秀深入讨论，请参见大卫·戈德堡的论文 [What Every Computer Scientist Should Know About Floating-Point Arithmetic](https://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.22.6768&rep=rep1&type=pdf)。
  * 有关浮点数的历史、理由和问题的更广泛文档，以及许多其他数值计算主题的讨论，请参阅 [collected writings](https://people.eecs.berkeley.edu/~wkahan/) 的 [William Kahan](https://en.wikipedia.org/wiki/William_Kahan)，通常被称为“浮点之父”。特别感兴趣的可能是 [An Interview with the Old Man of Floating-Point](https://people.eecs.berkeley.edu/~wkahan/ieee754status/754story.html)。

## Arbitrary Precision Arithmetic

为了允许对任意精度整数和浮点数进行计算，Julia 包装了 [GNU Multiple Precision Arithmetic Library (GMP)](https://gmplib.org) 和 [GNU MPFR Library](https://www.mpfr.org)。[`BigInt`](@ref) 和 [`BigFloat`](@ref) 类型在 Julia 中分别用于任意精度整数和浮点数。

构造函数用于从原始数值类型创建这些类型，[string literal](@ref non-standard-string-literals)、[`@big_str`](@ref) 或 [`parse`](@ref) 可以用于从 `AbstractString` 构造它们。当 `BigInt` 太大而无法适应其他内置整数类型时，也可以将其作为整数字面量输入。请注意，由于 `Base` 中没有无符号任意精度整数类型（在大多数情况下 `BigInt` 足够），可以使用十六进制、八进制和二进制字面量（除了十进制字面量）。

一旦创建，它们就可以与所有其他数值类型进行算术运算，这要归功于 Julia 的 [type promotion and conversion mechanism](@ref conversion-and-promotion)：

```jldoctest
julia> BigInt(typemax(Int64)) + 1
9223372036854775808

julia> big"123456789012345678901234567890" + 1
123456789012345678901234567891

julia> parse(BigInt, "123456789012345678901234567890") + 1
123456789012345678901234567891

julia> string(big"2"^200, base=16)
"100000000000000000000000000000000000000000000000000"

julia> 0x100000000000000000000000000000000-1 == typemax(UInt128)
true

julia> 0x000000000000000000000000000000000
0

julia> typeof(ans)
BigInt

julia> big"1.23456789012345678901"
1.234567890123456789010000000000000000000000000000000000000000000000000000000004

julia> parse(BigFloat, "1.23456789012345678901")
1.234567890123456789010000000000000000000000000000000000000000000000000000000004

julia> BigFloat(2.0^66) / 3
2.459565876494606882133333333333333333333333333333333333333333333333333333333344e+19

julia> factorial(BigInt(40))
815915283247897734345611269596115894272000000000
```

然而，上述原始类型与 [`BigInt`](@ref)/[`BigFloat`](@ref) 之间的类型提升不是自动的，必须明确说明。

```jldoctest
julia> x = typemin(Int64)
-9223372036854775808

julia> x = x - 1
9223372036854775807

julia> typeof(x)
Int64

julia> y = BigInt(typemin(Int64))
-9223372036854775808

julia> y = y - 1
-9223372036854775809

julia> typeof(y)
BigInt
```

[`BigFloat`](@ref) 操作的默认精度（以有效数字的位数表示）和舍入模式可以通过调用 [`setprecision`](@ref) 和 [`setrounding`](@ref) 全局更改，所有后续计算将考虑这些更改。 另外，精度或舍入也可以仅在特定代码块的执行过程中进行更改，方法是使用相同的函数并结合 `do` 块：

```jldoctest
julia> setrounding(BigFloat, RoundUp) do
           BigFloat(1) + parse(BigFloat, "0.1")
       end
1.100000000000000000000000000000000000000000000000000000000000000000000000000003

julia> setrounding(BigFloat, RoundDown) do
           BigFloat(1) + parse(BigFloat, "0.1")
       end
1.099999999999999999999999999999999999999999999999999999999999999999999999999986

julia> setprecision(40) do
           BigFloat(1) + parse(BigFloat, "0.1")
       end
1.1000000000004
```

!!! warning
    [`setprecision`](@ref) 或 [`setrounding`](@ref) 与 [`@big_str`](@ref) 之间的关系，可能并不直观，因为 `@big_str` 是一个宏。有关详细信息，请参阅 `4d61726b646f776e2e436f64652822222c2022406269675f7374722229_40726566` 文档。


## [Numeric Literal Coefficients](@id man-numeric-literal-coefficients)

为了使常见的数字公式和表达式更清晰，Julia 允许变量前面直接跟一个数字字面量，表示乘法。这使得编写多项式表达式更加简洁：

```jldoctest numeric-coefficients
julia> x = 3
3

julia> 2x^2 - 3x + 1
10

julia> 1.5x^2 - .5x + 1
13.0
```

它还使得编写指数函数变得更加优雅：

```jldoctest numeric-coefficients
julia> 2^2x
64
```

数字字面量系数的优先级略低于一元运算符，例如取负运算。因此 `-2x` 被解析为 `(-2) * x`，而 `√2x` 被解析为 `(√2) * x`。然而，当与指数运算结合时，数字字面量系数的解析方式与一元运算符相似。例如 `2^3x` 被解析为 `2^(3x)`，而 `2x^3` 被解析为 `2*(x^3)`。

数字字面量也可以作为括号表达式的系数：

```jldoctest numeric-coefficients
julia> 2(x-1)^2 - 3(x-1) + 1
3
```

!!! note
    数字字面量系数用于隐式乘法的优先级高于其他二元运算符，例如乘法（`*`）和除法（`/`、`\` 和 `//`）。这意味着，例如，`1 / 2im` 等于 `-0.5im`，而 `6 // 2(2 + 1)` 等于 `1 // 1`。


此外，带括号的表达式可以用作变量的系数，意味着将表达式与变量相乘：

```jldoctest numeric-coefficients
julia> (x-1)x
6
```

两个带括号的表达式的并列，或者在带括号的表达式前放置一个变量，都不能用来表示乘法：

```jldoctest numeric-coefficients
julia> (x-1)(x+1)
ERROR: MethodError: objects of type Int64 are not callable

julia> x(x+1)
ERROR: MethodError: objects of type Int64 are not callable
```

这两个表达式都被解释为函数应用：任何不是数字字面量的表达式，当紧接着一个括号时，都被解释为一个函数应用于括号中的值（有关函数的更多信息，请参见 [Functions](@ref)）。因此，在这两种情况下都会发生错误，因为左侧的值不是一个函数。

上述语法增强显著减少了在书写常见数学公式时产生的视觉噪音。请注意，数字字面量系数与其所乘的标识符或括号表达式之间不得有空格。

### Syntax Conflicts

并排的字面系数语法可能与某些数字字面语法发生冲突：十六进制、八进制和二进制整数字面以及浮点字面的工程记数法。以下是一些出现语法冲突的情况：

  * 十六进制整数字面量表达式 `0xff` 可以被解释为数字字面量 `0` 乘以变量 `xff`。类似的歧义也出现在八进制和二进制字面量中，例如 `0o777` 或 `0b01001010`。
  * 浮点字面量表达式 `1e10` 可以被解释为数字字面量 `1` 乘以变量 `e10`，同样适用于等效的 `E` 形式。
  * 32位浮点字面量表达式 `1.5f22` 可以被解释为数字字面量 `1.5` 乘以变量 `f22`。

在所有情况下，歧义都以将其解释为数字字面量的方式得到解决：

  * 以 `0x`/`0o`/`0b` 开头的表达式始终是十六进制/八进制/二进制字面量。
  * 以数字字面量开头，后跟 `e` 或 `E` 的表达式始终是浮点字面量。
  * 以数字字面量开头并后跟 `f` 的表达式始终是 32 位浮点字面量。

与 `E` 不同，`E` 在数字字面量中出于历史原因等同于 `e`，而 `F` 只是另一个字母，并且在数字字面量中不表现得像 `f`。因此，以数字字面量开头后跟 `F` 的表达式被解释为数字字面量乘以一个变量，这意味着，例如，`1.5F22` 等于 `1.5 * F22`。

## Literal zero and one

Julia 提供了返回与指定类型或给定变量类型相对应的字面量 0 和 1 的函数。

| Function          | Description                                      |
|:----------------- |:------------------------------------------------ |
| [`zero(x)`](@ref) | Literal zero of type `x` or type of variable `x` |
| [`one(x)`](@ref)  | Literal one of type `x` or type of variable `x`  |

这些函数在 [Numeric Comparisons](@ref) 中非常有用，以避免不必要的 [type conversion](@ref conversion-and-promotion) 带来的开销。

示例：

```jldoctest
julia> zero(Float32)
0.0f0

julia> zero(1.0)
0.0

julia> one(Int32)
1

julia> one(BigFloat)
1.0
```
