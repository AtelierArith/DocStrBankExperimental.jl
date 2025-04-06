# Mathematical Operations and Elementary Functions

Julia, tüm sayısal temel türleri arasında temel aritmetik ve bit düzeyindeki operatörlerin tam bir koleksiyonunu sunar ve ayrıca kapsamlı bir standart matematiksel fonksiyon koleksiyonunun taşınabilir, verimli uygulamalarını sağlar.

## Arithmetic Operators

Aşağıdaki [arithmetic operators](https://en.wikipedia.org/wiki/Arithmetic#Arithmetic_operations) tüm ilkel sayısal türlerde desteklenmektedir:

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

Bir tanımlayıcı veya parantezden hemen önce yerleştirilen bir sayısal literal, örneğin `2x` veya `2(x + y)`, diğer ikili işlemlerden daha yüksek önceliğe sahip bir çarpma olarak değerlendirilir. Ayrıntılar için [Numeric Literal Coefficients](@ref man-numeric-literal-coefficients)'e bakın.

Julia'nın terfi sistemi, argüman türlerinin karışımları üzerinde aritmetik işlemlerin "doğal olarak" ve otomatik olarak çalışmasını sağlar. Ayrıntılar için [Conversion and Promotion](@ref conversion-and-promotion)'e bakın.

÷ işareti, REPL veya Julia IDE'sine `\div<tab>` yazarak kolayca yazılabilir. Daha fazla bilgi için [manual section on Unicode input](@ref Unicode-Input)'e bakın.

İşte aritmetik operatörler kullanan bazı basit örnekler:

```jldoctest
julia> 1 + 2 + 3
6

julia> 1 - 2
-1

julia> 3*2/12
0.5
```

(Gelenek olarak, operatörlerin yanındaki diğer operatörlerden önce uygulanıyorsa, genellikle operatörleri daha sıkı bir şekilde aralıyoruz. Örneğin, ilk `x`'in negatif alındığını ve ardından `2`'nin bu sonuca eklendiğini yansıtmak için genellikle `-x + 2` şeklinde yazarız.)

Çarpma işlemlerinde `false`, *güçlü sıfır* olarak işlev görür:

```jldoctest
julia> NaN * false
0.0

julia> false * Inf
0.0
```

Bu, sıfır olduğu bilinen miktarlarda `NaN` değerlerinin yayılmasını önlemek için faydalıdır. Motivasyon için [Knuth (1992)](https://arxiv.org/abs/math/9205211)'e bakın.

## Boolean Operators

Aşağıdaki [Boolean operators](https://en.wikipedia.org/wiki/Boolean_algebra#Operations) [`Bool`](@ref) türleri desteklenmektedir:

| Expression | Name                                                    |
|:---------- |:------------------------------------------------------- |
| `!x`       | negation                                                |
| `x && y`   | [short-circuiting and](@ref man-conditional-evaluation) |
| `x \|\| y` | [short-circuiting or](@ref man-conditional-evaluation)  |

Negasyon `true`'yu `false`'a ve tersini değiştirir. Kısa devre işlemleri bağlantılı sayfada açıklanmıştır.

`Bool` bir tam sayı türüdür ve tüm olağan yükseltme kuralları ve sayısal operatörler de üzerinde tanımlıdır.

## Bitwise Operators

Aşağıdaki [bitwise operators](https://en.wikipedia.org/wiki/Bitwise_operation#Bitwise_operators) tüm ilkel tam sayı türlerinde desteklenmektedir:

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

İşte bit düzeyinde işleçlerle ilgili bazı örnekler:

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

Herhangi bir ikili aritmetik ve bit düzeyindeki operatörün, işlemin sonucunu sol operandına geri atayan bir güncelleme versiyonu da vardır. İkili operatörün güncelleme versiyonu, operatörden hemen sonra bir `=` yerleştirerek oluşturulur. Örneğin, `x += 3` yazmak, `x = x + 3` yazmakla eşdeğerdir:

```jldoctest
julia> x = 1
1

julia> x += 3
4

julia> x
4
```

Tüm ikili aritmetik ve bit düzeyindeki operatörlerin güncellenmiş sürümleri şunlardır:

```
+=  -=  *=  /=  \=  ÷=  %=  ^=  &=  |=  ⊻=  >>>=  >>=  <<=
```

!!! note
    Bir güncelleme operatörü, sol taraftaki değişkeni yeniden bağlar. Sonuç olarak, değişkenin türü değişebilir.

    ```jldoctest
    julia> x = 0x01; typeof(x)
    UInt8

    julia> x *= 2 # Same as x = x * 2
    2

    julia> typeof(x)
    Int64
    ```


## [Vectorized "dot" operators](@id man-dot-operators)

Her *her* ikili işlem için `^`, bir "nokta" işlemi `.^` vardır ki bu *otomatik olarak* diziler üzerinde `^` eleman bazında gerçekleştirmek için tanımlanmıştır. Örneğin, `[1, 2, 3] ^ 3` tanımlı değildir, çünkü bir (dörtgen olmayan) dizinin "küpleme" için standart matematiksel bir anlamı yoktur, ancak `[1, 2, 3] .^ 3` eleman bazında (veya "vektörleştirilmiş") sonucu `[1^3, 2^3, 3^3]` hesaplamak olarak tanımlanmıştır. Benzer şekilde, `!` veya `√` gibi tekil operatörler için, operatörü eleman bazında uygulayan bir `.√` vardır.

```jldoctest
julia> [1, 2, 3] .^ 3
3-element Vector{Int64}:
  1
  8
 27
```

Daha spesifik olarak, `a .^ b` ifadesi ["dot" call](@ref man-vectorized) `(^).(a,b)` olarak yorumlanır; bu, [broadcast](@ref Broadcasting) işlemini gerçekleştirir: dizileri ve skalarları, aynı boyuttaki dizileri (işlemi eleman bazında gerçekleştirerek) ve hatta farklı şekillerdeki dizileri (örneğin, satır ve sütun vektörlerini bir matris üretmek için birleştirerek) birleştirebilir. Dahası, tüm vektörleştirilmiş "nokta çağrıları" gibi, bu "nokta operatörleri" *birleştirilmektedir*. Örneğin, bir dizi `A` için `2 .* A.^2 .+ sin.(A)` (veya eşdeğer olarak `@. 2A^2 + sin(A)`, [`@.`](@ref @__dot__) makrosunu kullanarak) hesapladığınızda, `A` üzerinde *tek* bir döngü gerçekleştirir ve `A`'nın her bir elemanı `a` için `2a^2 + sin(a)` hesaplar. Özellikle, `f.(g.(x))` gibi iç içe nokta çağrıları birleştirilir ve `x .+ 3 .* x.^2` gibi "bitişik" ikili operatörler, iç içe nokta çağrıları `(+).(x, (*).(3, (^).(x, 2)))` ile eşdeğerdir.

Furthermore, "dotted" updating operators like `a .+= b` (or `@. a += b`) are parsed as `a .= a .+ b`, where `.=` is a fused *in-place* assignment operation (see the [dot syntax documentation](@ref man-vectorized)).

Not edin nokta sözdizimi, kullanıcı tanımlı operatörler için de geçerlidir. Örneğin, `⊗(A, B) = kron(A, B)` tanımlarsanız, Kronecker çarpımları için `A ⊗ B` şeklinde kullanışlı bir infiks sözdizimi elde edersiniz ([`kron`](@ref)). Bu durumda, `[A, B] .⊗ [C, D]` ifadesi, ek bir kodlama gerektirmeden `[A⊗C, B⊗D]` hesaplayacaktır.

Nokta operatörlerini sayısal sabitlerle birleştirmek belirsiz olabilir. Örneğin, `1.+x` ifadesinin `1. + x` mi yoksa `1 .+ x` mi olduğu net değildir. Bu nedenle bu sözdizimi yasaklanmıştır ve bu tür durumlarda operatör etrafında boşluklar kullanılmalıdır.

## Numeric Comparisons

Tüm temel sayısal türler için standart karşılaştırma işlemleri tanımlanmıştır:

| Operator                     | Name                     |
|:---------------------------- |:------------------------ |
| [`==`](@ref)                 | equality                 |
| [`!=`](@ref), [`≠`](@ref !=) | inequality               |
| [`<`](@ref)                  | less than                |
| [`<=`](@ref), [`≤`](@ref <=) | less than or equal to    |
| [`>`](@ref)                  | greater than             |
| [`>=`](@ref), [`≥`](@ref >=) | greater than or equal to |

İşte bazı basit örnekler:

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

Tam sayılar standart şekilde - bitlerin karşılaştırılmasıyla - karşılaştırılır. Kayan noktalı sayılar ise [IEEE 754 standard](https://en.wikipedia.org/wiki/IEEE_754-2008)'ye göre karşılaştırılır:

  * Sonlu sayılar, olağan şekilde sıralanmıştır.
  * Pozitif sıfır, negatif sıfırdan eşit ama daha büyük değildir.
  * `Inf`, kendisiyle eşittir ve `NaN` hariç her şeyden büyüktür.
  * `-Inf` kendisiyle eşittir ve `NaN` hariç her şeyden küçüktür.
  * `NaN` kendisi de dahil olmak üzere hiçbir şeye eşit, daha az veya daha fazla değildir.

Son nokta potansiyel olarak şaşırtıcıdır ve bu nedenle dikkate değer:

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

ve ve baş ağrısına neden olabilir [arrays](@ref man-multi-dim-arrays):

```jldoctest
julia> [1 NaN] == [1 NaN]
false
```

Julia, özel değerler için sayıları test etmek üzere ek fonksiyonlar sağlar; bu, hash anahtarı karşılaştırmaları gibi durumlarda faydalı olabilir:

| Function                | Tests if                  |
|:----------------------- |:------------------------- |
| [`isequal(x, y)`](@ref) | `x` and `y` are identical |
| [`isfinite(x)`](@ref)   | `x` is a finite number    |
| [`isinf(x)`](@ref)      | `x` is infinite           |
| [`isnan(x)`](@ref)      | `x` is not a number       |

[`isequal`](@ref) `NaN`'leri birbirine eşit kabul eder:

```jldoctest
julia> isequal(NaN, NaN)
true

julia> isequal([1 NaN], [1 NaN])
true

julia> isequal(NaN, NaN32)
true
```

`isequal` işaretli sıfırları ayırt etmek için de kullanılabilir:

```jldoctest
julia> -0.0 == 0.0
true

julia> isequal(-0.0, 0.0)
false
```

İmzalı tam sayılar, imzasız tam sayılar ve float'lar arasında karışık tür karşılaştırmaları zorlayıcı olabilir. Julia'nın bunları doğru bir şekilde yapmasını sağlamak için büyük bir özen gösterilmiştir.

Diğer türler için, `isequal` varsayılan olarak [`==`](@ref) çağrısını yapar, bu nedenle kendi türleriniz için eşitliği tanımlamak istiyorsanız yalnızca bir `4d61726b646f776e2e436f64652822222c20223d3d2229_40726566` yöntemi eklemeniz gerekir. Kendi eşitlik fonksiyonunuzu tanımlarsanız, `isequal(x,y)` ifadesinin `hash(x) == hash(y)` anlamına gelmesini sağlamak için muhtemelen karşılık gelen bir [`hash`](@ref) yöntemi tanımlamalısınız.

### Chaining comparisons

Diğer dillerin çoğunun aksine, [notable exception of Python](https://en.wikipedia.org/wiki/Python_syntax_and_semantics#Comparison_operators) ile karşılaştırmalar keyfi olarak zincirlenebilir:

```jldoctest
julia> 1 < 2 <= 2 < 3 == 3 > 2 >= 1 == 1 < 3 != 5
true
```

Karşılaştırmaları zincirleme, sayısal kodda genellikle oldukça kullanışlıdır. Zincirleme karşılaştırmalar, skalar karşılaştırmalar için `&&` operatörünü ve eleman bazında karşılaştırmalar için [`&`](@ref) operatörünü kullanır; bu, diziler üzerinde çalışmasına olanak tanır. Örneğin, `0 .< A .< 1` ifadesi, `A`'nın karşılık gelen elemanlarının 0 ile 1 arasında olduğu yerlerde doğru olan bir boolean dizisi verir.

Zincirleme karşılaştırmaların değerlendirme davranışını not edin:

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

Orta ifade yalnızca bir kez değerlendirilir, oysa ifade `v(1) < v(2) && v(2) <= v(3)` şeklinde yazılmış olsaydı iki kez değerlendirilirdi. Ancak, zincirleme karşılaştırmalardaki değerlendirme sırası belirsizdir. Zincirleme karşılaştırmalarda yan etkileri (örneğin, yazdırma gibi) kullanmamanız şiddetle önerilir. Yan etkiler gerekiyorsa, kısa devre `&&` operatörü açıkça kullanılmalıdır (bkz. [Short-Circuit Evaluation](@ref)).

### Elementary Functions

Julia, matematiksel fonksiyonlar ve operatörlerin kapsamlı bir koleksiyonunu sunar. Bu matematiksel işlemler, mantıklı tanımlara izin veren en geniş sayısal değer sınıfı üzerinde tanımlanmıştır; bu, mantıklı tanımların anlamlı olduğu yerlerde tam sayılar, kayan noktalı sayılar, rasyonel sayılar ve karmaşık sayıları içerir.

Ayrıca, bu fonksiyonlar (herhangi bir Julia fonksiyonu gibi) [dot syntax](@ref man-vectorized) `f.(A)` ile dizilere ve diğer koleksiyonlara "vektörleştirilmiş" bir şekilde uygulanabilir; örneğin, `sin.(A)` bir dizi `A`'nın her bir elemanının sinüsünü hesaplayacaktır.

## Operator Precedence and Associativity

Julia, aşağıdaki işlem sırasını ve birleştirme kurallarını, en yüksek öncelikten en düşük önceliğe doğru uygular:

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

Tam bir liste için *her* Julia operatörünün önceliği, bu dosyanın en üstüne bakın: [`src/julia-parser.scm`](https://github.com/JuliaLang/julia/blob/master/src/julia-parser.scm). Orada bazı operatörlerin `Base` modülünde tanımlanmadığını, ancak standart kütüphaneler, paketler veya kullanıcı kodu tarafından tanımlanabileceğini unutmayın.

Verilen herhangi bir operatör için sayısal önceliği, daha yüksek sayıların önceliği aldığı yerleşik `Base.operator_precedence` fonksiyonu aracılığıyla da bulabilirsiniz:

```jldoctest
julia> Base.operator_precedence(:+), Base.operator_precedence(:*), Base.operator_precedence(:.)
(11, 12, 17)

julia> Base.operator_precedence(:sin), Base.operator_precedence(:+=), Base.operator_precedence(:(=))  # (Note the necessary parens on `:(=)`)
(0, 1, 1)
```

Bir operatör birleşimliliğini temsil eden bir sembol, yerleşik `Base.operator_associativity` fonksiyonu çağrılarak da bulunabilir:

```jldoctest
julia> Base.operator_associativity(:-), Base.operator_associativity(:+), Base.operator_associativity(:^)
(:left, :none, :right)

julia> Base.operator_associativity(:⊗), Base.operator_associativity(:sin), Base.operator_associativity(:→)
(:left, :none, :right)
```

Not edin ki `:sin` gibi semboller öncelik `0` döndürür. Bu değer geçersiz operatörleri temsil eder ve en düşük öncelikli operatörleri değil. Benzer şekilde, bu tür operatörlere `:none` birliktelik atanır.

[Numeric literal coefficients](@ref man-numeric-literal-coefficients), örneğin `2x`, diğer ikili işlemlerden daha yüksek önceliğe sahip çarpımlar olarak değerlendirilir, `^` hariç, burada yalnızca üslü işlem olarak daha yüksek önceliğe sahiptir.

```jldoctest
julia> x = 3; 2x^2
18

julia> x = 3; 2^2x
64
```

Juxtapozisyon, üstelere etrafında aynı doğal asimetrik yapıya sahip olan bir unary operatör gibi ayrıştırılır: `-x^y` ve `2x^y`, `-(x^y)` ve `2(x^y)` olarak ayrıştırılırken, `x^-y` ve `x^2y`, `x^(-y)` ve `x^(2y)` olarak ayrıştırılır.

## Numerical Conversions

Julia, üç farklı sayısal dönüştürme biçimini destekler; bu biçimler, kesin olmayan dönüşümlerin işlenişinde farklılık gösterir.

  * `T(x)` veya `convert(T, x)` notasyonu, `x`'i `T` türünde bir değere dönüştürür.

      * Eğer `T` bir kayan nokta türüyse, sonuç en yakın temsil edilebilir değer olup, bu pozitif veya negatif sonsuzluk olabilir.
      * Eğer `T` bir tam sayı türüyse, `x` `T` tarafından temsil edilemezse bir `InexactError` hatası oluşur.
  * `x % T` bir tam sayıyı `x`'in `2^n` modülüne göre `T` tam sayı türüne uygun bir değere dönüştürür; burada `n`, `T`'deki bit sayısını ifade eder. Diğer bir deyişle, ikili temsil, sığacak şekilde kesilir.
  * [Rounding functions](@ref) bir `T` türünü isteğe bağlı bir argüman olarak alır. Örneğin, `round(Int,x)` ifadesi `Int(round(x))` için bir kısayoldur.

Aşağıdaki örnekler farklı biçimleri göstermektedir.

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

[Conversion and Promotion](@ref conversion-and-promotion) için kendi dönüşümlerinizi ve promosyonlarınızı nasıl tanımlayacağınızı görün.

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

[`hypot`](@ref), [`expm1`](@ref), ve [`log1p`](@ref) gibi fonksiyonların neden gerekli ve faydalı olduğuna dair bir genel bakış için John D. Cook'un bu konudaki mükemmel iki blog yazısına bakın: [expm1, log1p, erfc](https://www.johndcook.com/blog/2010/06/07/math-library-functions-that-seem-unnecessary/) ve [hypot](https://www.johndcook.com/blog/2010/06/02/whats-so-hard-about-finding-a-hypotenuse/).

### Trigonometric and hyperbolic functions

Tüm standart trigonometrik ve hiperbolik fonksiyonlar da tanımlanmıştır:

```
sin    cos    tan    cot    sec    csc
sinh   cosh   tanh   coth   sech   csch
asin   acos   atan   acot   asec   acsc
asinh  acosh  atanh  acoth  asech  acsch
sinc   cosc
```

Bunlar, [`atan`](@ref) geleneksel [`atan2`](https://en.wikipedia.org/wiki/Atan2) fonksiyonuna karşılık gelen iki argümanı da kabul eden tek argümanlı fonksiyonlardır.

Ayrıca, [`sinpi(x)`](@ref) ve [`cospi(x)`](@ref) daha doğru hesaplamalar için [`sin(pi * x)`](@ref) ve [`cos(pi * x)`](@ref) ile sırasıyla sağlanmıştır.

Derece yerine radyan kullanarak trigonometrik fonksiyonları hesaplamak için, fonksiyonun sonuna `d` ekleyin. Örneğin, [`sind(x)`](@ref) ifadesi, `x`'in derece cinsinden belirtildiği durumda `x`'in sinüsünü hesaplar. Derece varyantlarına sahip trigonometrik fonksiyonların tam listesi şudur:

```
sind   cosd   tand   cotd   secd   cscd
asind  acosd  atand  acotd  asecd  acscd
```

### Special functions

Birçok diğer özel matematiksel fonksiyon, [SpecialFunctions.jl](https://github.com/JuliaMath/SpecialFunctions.jl) paketinde sağlanmaktadır.
