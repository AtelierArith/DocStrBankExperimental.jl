# Complex and Rational Numbers

Julia 包含了预定义的复数和有理数类型，并支持所有标准的 [Mathematical Operations and Elementary Functions](@ref)。[Conversion and Promotion](@ref conversion-and-promotion) 被定义为在任何组合的预定义数值类型上进行操作时，无论是原始类型还是复合类型，都能按预期行为运行。

## Complex Numbers

全局常量 [`im`](@ref) 绑定到复数 *i*，表示 -1 的主平方根。（由于数学家的 `i` 或工程师的 `j` 是如此流行的索引变量名称，因此拒绝将它们用作此全局常量。）由于 Julia 允许数字字面量为 [juxtaposed with identifiers as coefficients](@ref man-numeric-literal-coefficients)，因此此绑定足以为复数提供方便的语法，类似于传统的数学符号：

```jldoctest
julia> 1+2im
1 + 2im
```

您可以对复数执行所有标准的算术运算：

```jldoctest
julia> (1 + 2im)*(2 - 3im)
8 + 1im

julia> (1 + 2im)/(1 - 2im)
-0.6 + 0.8im

julia> (1 + 2im) + (1 - 2im)
2 + 0im

julia> (-3 + 2im) - (5 - 1im)
-8 + 3im

julia> (-1 + 2im)^2
-3 - 4im

julia> (-1 + 2im)^2.5
2.729624464784009 - 6.9606644595719im

julia> (-1 + 2im)^(1 + 1im)
-0.27910381075826657 + 0.08708053414102428im

julia> 3(2 - 5im)
6 - 15im

julia> 3(2 - 5im)^2
-63 - 60im

julia> 3(2 - 5im)^-1.0
0.20689655172413793 + 0.5172413793103449im
```

提升机制确保不同类型的操作数组合可以正常工作：

```jldoctest
julia> 2(1 - 1im)
2 - 2im

julia> (2 + 3im) - 1
1 + 3im

julia> (1 + 2im) + 0.5
1.5 + 2.0im

julia> (2 + 3im) - 0.5im
2.0 + 2.5im

julia> 0.75(1 + 2im)
0.75 + 1.5im

julia> (2 + 3im) / 2
1.0 + 1.5im

julia> (1 - 3im) / (2 + 2im)
-0.5 - 1.0im

julia> 2im^2
-2 + 0im

julia> 1 + 3/4im
1.0 - 0.75im
```

注意到 `3/4im == 3/(4*im) == -(3/4*im)`，因为字面系数的优先级高于除法。

提供了用于操作复数值的标准函数：

```jldoctest
julia> z = 1 + 2im
1 + 2im

julia> real(1 + 2im) # real part of z
1

julia> imag(1 + 2im) # imaginary part of z
2

julia> conj(1 + 2im) # complex conjugate of z
1 - 2im

julia> abs(1 + 2im) # absolute value of z
2.23606797749979

julia> abs2(1 + 2im) # squared absolute value
5

julia> angle(1 + 2im) # phase angle in radians
1.1071487177940904
```

如往常一样，复数的绝对值（[`abs`](@ref)）是其与零的距离。[`abs2`](@ref) 给出了绝对值的平方，这对于复数特别有用，因为它避免了取平方根。[`angle`](@ref) 返回以弧度表示的相位角（也称为 *argument* 或 *arg* 函数）。复数的其他完整范围 [Elementary Functions](@ref) 也被定义：

```jldoctest
julia> sqrt(1im)
0.7071067811865476 + 0.7071067811865475im

julia> sqrt(1 + 2im)
1.272019649514069 + 0.7861513777574233im

julia> cos(1 + 2im)
2.0327230070196656 - 3.0518977991517997im

julia> exp(1 + 2im)
-1.1312043837568135 + 2.4717266720048188im

julia> sinh(1 + 2im)
-0.4890562590412937 + 1.4031192506220405im
```

请注意，数学函数在应用于实数时通常返回实值，而在应用于复数时返回复值。例如，[`sqrt`](@ref) 在应用于 `-1` 和 `-1 + 0im` 时表现不同，尽管 `-1 == -1 + 0im`：

```jldoctest
julia> sqrt(-1)
ERROR: DomainError with -1.0:
sqrt was called with a negative real argument but will only return a complex result if called with a complex argument. Try sqrt(Complex(x)).
Stacktrace:
[...]

julia> sqrt(-1 + 0im)
0.0 + 1.0im
```

[literal numeric coefficient notation](@ref man-numeric-literal-coefficients) 在从变量构造复数时不起作用。相反，乘法必须明确写出：

```jldoctest
julia> a = 1; b = 2; a + b*im
1 + 2im
```

然而，这*并不*推荐。相反，使用更高效的 [`complex`](@ref) 函数直接从其实部和虚部构造复值：

```jldoctest
julia> a = 1; b = 2; complex(a, b)
1 + 2im
```

此构造避免了乘法和加法运算。

[`Inf`](@ref) 和 [`NaN`](@ref) 在复数的实部和虚部中传播，如 [Special floating-point values](@ref) 部分所述：

```jldoctest
julia> 1 + Inf*im
1.0 + Inf*im

julia> 1 + NaN*im
1.0 + NaN*im
```

## Rational Numbers

朱莉亚有一个有理数类型，用于表示整数的精确比率。有理数是使用 [`//`](@ref) 运算符构造的：

```jldoctest
julia> 2//3
2//3
```

如果一个有理数的分子和分母有公因子，它们会被约简到最简形式，使得分母为非负数：

```jldoctest
julia> 6//9
2//3

julia> -4//8
-1//2

julia> 5//-15
-1//3

julia> -4//-12
1//3
```

This normalized form for a ratio of integers is unique, so equality of rational values can be tested by checking for equality of the numerator and denominator. The standardized numerator and denominator of a rational value can be extracted using the [`numerator`](@ref) and [`denominator`](@ref) functions:

```jldoctest
julia> numerator(2//3)
2

julia> denominator(2//3)
3
```

直接比较分子和分母通常不是必要的，因为标准的算术和比较运算是为有理值定义的：

```jldoctest
julia> 2//3 == 6//9
true

julia> 2//3 == 9//27
false

julia> 3//7 < 1//2
true

julia> 3//4 > 2//3
true

julia> 2//4 + 1//6
2//3

julia> 5//12 - 1//4
1//6

julia> 5//8 * 3//12
5//32

julia> 6//5 / 10//7
21//25
```

有理数可以很容易地转换为浮点数：

```jldoctest
julia> float(3//4)
0.75
```

从有理数到浮点数的转换遵循以下恒等式，对于任何整数值的 `a` 和 `b`，除非 `a==0 && b <= 0`：

```jldoctest
julia> a = 1; b = 2;

julia> isequal(float(a//b), a/b)
true

julia> a, b = 0, 0
(0, 0)

julia> float(a//b)
ERROR: ArgumentError: invalid rational: zero(Int64)//zero(Int64)
Stacktrace:
[...]

julia> a/b
NaN

julia> a, b = 0, -1
(0, -1)

julia> float(a//b), a/b
(0.0, -0.0)
```

构造无限的有理值是可以接受的：

```jldoctest
julia> 5//0
1//0

julia> x = -3//0
-1//0

julia> typeof(x)
Rational{Int64}
```

尝试构造一个 [`NaN`](@ref) 有理值，但这是无效的：

```jldoctest
julia> 0//0
ERROR: ArgumentError: invalid rational: zero(Int64)//zero(Int64)
Stacktrace:
[...]
```

如往常一样，提升系统使与其他数值类型的交互变得轻而易举：

```jldoctest
julia> 3//5 + 1
8//5

julia> 3//5 - 0.5
0.09999999999999998

julia> 2//7 * (1 + 2im)
2//7 + 4//7*im

julia> 2//7 * (1.5 + 2im)
0.42857142857142855 + 0.5714285714285714im

julia> 3//2 / (1 + 2im)
3//10 - 3//5*im

julia> 1//2 + 2im
1//2 + 2//1*im

julia> 1 + 2//3im
1//1 - 2//3*im

julia> 0.5 == 1//2
true

julia> 0.33 == 1//3
false

julia> 0.33 < 1//3
true

julia> 1//3 - 0.33
0.0033333333333332993
```
