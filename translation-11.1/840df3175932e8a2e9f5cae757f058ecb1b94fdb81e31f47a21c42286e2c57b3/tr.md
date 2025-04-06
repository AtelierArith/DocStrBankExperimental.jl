# Complex and Rational Numbers

Julia, karmaşık ve rasyonel sayılar için önceden tanımlanmış türler içerir ve bunlar üzerinde tüm standart [Mathematical Operations and Elementary Functions](@ref) desteklenir. [Conversion and Promotion](@ref conversion-and-promotion) önceden tanımlanmış sayısal türlerin herhangi bir kombinasyonu üzerinde, ister ilkel ister bileşik olsun, işlemlerin beklenildiği gibi davranmasını sağlamak için tanımlanmıştır.

## Complex Numbers

Küresel sabit [`im`](@ref), -1'in ana karekökünü temsil eden *i* karmaşık sayısına bağlanmıştır. (Bu küresel sabit için matematikçilerin `i` veya mühendislerin `j` kullanılması, bu kadar popüler indeks değişkeni adları olduğu için reddedilmiştir.) Julia, sayısal literalleri [juxtaposed with identifiers as coefficients](@ref man-numeric-literal-coefficients) olarak tanımlamaya izin verdiğinden, bu bağlama karmaşık sayılar için geleneksel matematiksel notasyona benzer bir sözdizimi sağlamak için yeterlidir:

```jldoctest
julia> 1+2im
1 + 2im
```

Karmaşık sayılarla tüm standart aritmetik işlemleri gerçekleştirebilirsiniz:

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

Terfi mekanizması, farklı türdeki operandların kombinasyonlarının sorunsuz bir şekilde çalışmasını sağlar:

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

Not edin ki `3/4im == 3/(4*im) == -(3/4*im)`, çünkü bir literal katsayı bölmeden daha sıkı bağlanır.

Standart karmaşık değerleri manipüle etmek için işlevler sağlanmıştır:

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

Her zamanki gibi, bir karmaşık sayının mutlak değeri ([`abs`](@ref)) sıfıra olan mesafesidir. [`abs2`](@ref) mutlak değerin karesini verir ve karmaşık sayılar için özellikle kullanışlıdır çünkü karekök alma işlemini atlar. [`angle`](@ref) radyan cinsinden faz açısını döndürür (aynı zamanda *argüman* veya *arg* fonksiyonu olarak da bilinir). Karmaşık sayılar için diğer [Elementary Functions](@ref) tanımları da mevcuttur:

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

Matematiksel fonksiyonların genellikle gerçek sayılara uygulandıklarında gerçek değerler, karmaşık sayılara uygulandıklarında ise karmaşık değerler döndürdüğünü unutmayın. Örneğin, [`sqrt`](@ref) `-1` ile `-1 + 0im`'e uygulandığında farklı davranır, oysa `-1 == -1 + 0im`'dir:

```jldoctest
julia> sqrt(-1)
ERROR: DomainError with -1.0:
sqrt was called with a negative real argument but will only return a complex result if called with a complex argument. Try sqrt(Complex(x)).
Stacktrace:
[...]

julia> sqrt(-1 + 0im)
0.0 + 1.0im
```

[literal numeric coefficient notation](@ref man-numeric-literal-coefficients) karmaşık bir sayı oluşturulurken değişkenlerden çalışmaz. Bunun yerine, çarpma açıkça yazılmalıdır:

```jldoctest
julia> a = 1; b = 2; a + b*im
1 + 2im
```

Ancak, bu *tavsiye edilmez*. Bunun yerine, karmaşık bir değeri doğrudan reel ve sanal parçalarından oluşturmak için daha verimli [`complex`](@ref) fonksiyonunu kullanın:

```jldoctest
julia> a = 1; b = 2; complex(a, b)
1 + 2im
```

Bu yapı çarpma ve toplama işlemlerinden kaçınır.

[`Inf`](@ref) ve [`NaN`](@ref) karmaşık sayılarda karmaşık sayının reel ve sanal kısımlarında [Special floating-point values](@ref) bölümünde açıklandığı gibi yayılır:

```jldoctest
julia> 1 + Inf*im
1.0 + Inf*im

julia> 1 + NaN*im
1.0 + NaN*im
```

## Rational Numbers

Julia, tam sayıları tam oranlarını temsil etmek için bir rasyonel sayı türüne sahiptir. Rasyoneller, [`//`](@ref) operatörü kullanılarak oluşturulur:

```jldoctest
julia> 2//3
2//3
```

Eğer bir rasyonel sayının payı ve paydası ortak çarpanlara sahipse, bunlar en düşük terimlere indirgenir ve payda negatif olmamalıdır:

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

Bu tam sayılar oranı için normalize edilmiş form benzersizdir, bu nedenle rasyonel değerlerin eşitliği, pay ve paydanın eşitliğini kontrol ederek test edilebilir. Bir rasyonel değerin standartlaştırılmış payı ve paydası, [`numerator`](@ref) ve [`denominator`](@ref) fonksiyonları kullanılarak çıkarılabilir:

```jldoctest
julia> numerator(2//3)
2

julia> denominator(2//3)
3
```

Payda ve payın doğrudan karşılaştırılması genellikle gerekli değildir, çünkü standart aritmetik ve karşılaştırma işlemleri rasyonel değerler için tanımlanmıştır:

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

Rasyoneller kolayca kayan noktalı sayılara dönüştürülebilir:

```jldoctest
julia> float(3//4)
0.75
```

Rasyonel sayılardan kayan noktalı sayılara dönüşüm, `a` ve `b` için herhangi bir tam sayı değeri için aşağıdaki kimliği korur, yalnızca `a==0 && b <= 0` durumunda değil:

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

Sonsuz rasyonel değerler oluşturmak kabul edilebilir:

```jldoctest
julia> 5//0
1//0

julia> x = -3//0
-1//0

julia> typeof(x)
Rational{Int64}
```

[`NaN`](@ref) rasyonel değeri oluşturmaya çalışıyorum, ancak geçersiz:

```jldoctest
julia> 0//0
ERROR: ArgumentError: invalid rational: zero(Int64)//zero(Int64)
Stacktrace:
[...]
```

Her zamanki gibi, terfi sistemi diğer sayısal türlerle etkileşimleri zahmetsiz hale getirir:

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
