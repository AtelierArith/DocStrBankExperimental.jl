# Integers and Floating-Point Numbers

Tam sayılar ve ondalık değerler, aritmetik ve hesaplamanın temel yapı taşlarıdır. Bu tür değerlerin yerleşik temsilleri sayısal ilkelere denir, oysa tam sayılar ve ondalık sayıların kodda anlık değerler olarak temsilleri sayısal literaller olarak bilinir. Örneğin, `1` bir tam sayı literali iken, `1.0` bir ondalık sayı literali; bunların bellek içindeki ikili temsilleri nesneler olarak sayısal ilkelerdir.

Julia, geniş bir ilkel sayısal tür yelpazesi sunar ve bunlar üzerinde tanımlı bir dizi aritmetik ve bit düzeyinde operatör ile standart matematiksel fonksiyonlar mevcuttur. Bu, modern bilgisayarlarda yerel olarak desteklenen sayısal türler ve işlemlerle doğrudan eşleşir ve böylece Julia'nın hesaplama kaynaklarından tam anlamıyla yararlanmasına olanak tanır. Ayrıca, Julia, yerel donanım temsillerinde etkili bir şekilde temsil edilemeyen sayısal değerler üzerinde işlemler gerçekleştirebilen [Arbitrary Precision Arithmetic](@ref) yazılım desteği sağlar, ancak bu, görece daha yavaş bir performans maliyetiyle gelir.

Aşağıdakiler Julia'nın temel sayısal türleridir:

  * **Tam sayılar:**

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

  * **Kayan noktalı türler:**

| Type              | Precision                                                                      | Number of bits |
|:----------------- |:------------------------------------------------------------------------------ |:-------------- |
| [`Float16`](@ref) | [half](https://en.wikipedia.org/wiki/Half-precision_floating-point_format)     | 16             |
| [`Float32`](@ref) | [single](https://en.wikipedia.org/wiki/Single_precision_floating-point_format) | 32             |
| [`Float64`](@ref) | [double](https://en.wikipedia.org/wiki/Double_precision_floating-point_format) | 64             |

Ayrıca, [Complex and Rational Numbers](@ref) için tam destek, bu ilkel sayısal türlerin üzerine inşa edilmiştir. Tüm sayısal türler, esnek, kullanıcı genişletilebilir [type promotion system](@ref conversion-and-promotion) sayesinde açık bir tür dönüştürmesi olmadan doğal olarak etkileşimde bulunur.

## Integers

Tam sayılar standart şekilde temsil edilir:

```jldoctest
julia> 1
1

julia> 1234
1234
```

Tam sayısı literali için varsayılan tür, hedef sistemin 32 bit mimarisi mi yoksa 64 bit mimarisi mi olduğuna bağlıdır:

```julia-repl
# 32-bit system:
julia> typeof(1)
Int32

# 64-bit system:
julia> typeof(1)
Int64
```

Julia iç değişkeni [`Sys.WORD_SIZE`](@ref), hedef sistemin 32-bit mi yoksa 64-bit mi olduğunu gösterir:

```julia-repl
# 32-bit system:
julia> Sys.WORD_SIZE
32

# 64-bit system:
julia> Sys.WORD_SIZE
64
```

Julia ayrıca sistemin imzalı ve imzasız yerel tam sayı türleri için takma ad olan `Int` ve `UInt` türlerini tanımlar:

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

64 bit'ler ile temsil edilebilen ancak yalnızca 32 bit kullanılarak temsil edilemeyen daha büyük tam sayılar her zaman sistem türünden bağımsız olarak 64 bit tam sayılar oluşturur:

```jldoctest
# 32-bit or 64-bit system:
julia> typeof(3000000000)
Int64
```

İşaretsiz tam sayılar, `0x` ön eki ve onaltılık (taban 16) rakamlar `0-9a-f` kullanılarak girilir ve çıkarılır (büyük harfli rakamlar `A-F` girdi için de çalışır). İşaretsiz değerin boyutu, kullanılan onaltılık rakam sayısıyla belirlenir:

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

Bu davranış, birinin tam sayı değerleri için işaretsiz onaltılık literaller kullandığında, genellikle bunları yalnızca bir tam sayı değeri olarak değil, sabit bir sayısal bayt dizisini temsil etmek için kullandığı gözlemi üzerine kuruludur.

İkili ve sekizli sayılar da desteklenmektedir:

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

Hexadecimal literaller için, ikili ve sekizli literaller işaretsiz tam sayı türleri üretir. İkili veri öğesinin boyutu, eğer literalin baştaki rakamı `0` değilse, gereken en küçük boyuttur. Başta sıfırlar olduğunda, boyut, aynı uzunluğa sahip ancak baştaki rakamı `1` olan bir literalin gereken en küçük boyutu ile belirlenir. Bu, demektir ki:

  * `0x1` ve `0x12` `UInt8` literallerdir,
  * `0x123` ve `0x1234` `UInt16` literallerdir,
  * `0x12345` ve `0x12345678` `UInt32` literallerdir,
  * `0x123456789` ve `0x1234567890adcdef` `UInt64` literalleri, vb.

Önde gelen sıfır rakamları değere katkıda bulunmasa bile, bir literalın depolama boyutunu belirlemek için sayılır. Bu nedenle `0x01` bir `UInt8` iken `0x0001` bir `UInt16`'dır.

Bu, kullanıcının boyutu kontrol etmesine olanak tanır.

`UInt128` değerleri olarak temsil edilemeyecek kadar büyük tamsayıları kodlayan ( `0x` ile başlayan) işaretsiz literaller, bunun yerine `BigInt` değerleri oluşturacaktır. Bu işaretsiz bir tür değildir, ancak bu kadar büyük tamsayı değerlerini temsil edebilecek tek yerleşik türdür.

İkili, sekizli ve onaltılı sayısal ifadeler, işaretsiz sayısal ifadenin hemen önünde bir `-` ile işaretlenebilir. Bu, işaretsiz sayısal ifadenin üreteceği aynı boyutta işaretsiz bir tam sayı üretir ve değerin iki'nin tamamlayıcısını alır:

```jldoctest
julia> -0x2
0xfe

julia> -0x0002
0xfffe
```

Temel sayısal türlerin, örneğin tam sayıların, temsil edilebilen minimum ve maksimum değerleri [`typemin`](@ref) ve [`typemax`](@ref) fonksiyonlarıyla verilmektedir:

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

[`typemin`](@ref) ve [`typemax`](@ref) tarafından döndürülen değerler her zaman verilen argüman türündedir. (Yukarıdaki ifade, [for loops](@ref man-loops), [Strings](@ref man-strings) ve [Interpolation](@ref string-interpolation) dahil olmak üzere henüz tanıtılmamış birkaç özellik kullanmaktadır, ancak bazı mevcut programlama deneyimine sahip kullanıcılar için anlaması oldukça kolay olmalıdır.)

### Overflow behavior

Julia'da, belirli bir türün temsil edilebilen maksimum değerini aşmak, bir sarma davranışına yol açar:

```jldoctest
julia> x = typemax(Int64)
9223372036854775807

julia> x + 1
-9223372036854775808

julia> x + 1 == typemin(Int64)
true
```

Aritmetik işlemler, Julia'nın tam sayı türleri ile [modular arithmetic](https://en.wikipedia.org/wiki/Modular_arithmetic) ile gerçekleştirilir ve modern bilgisayar donanımındaki tam sayı aritmetiğinin özelliklerini yansıtır. Taşma olasılığının olduğu senaryolarda, bu tür taşmalardan kaynaklanabilecek sarılma etkilerini açıkça kontrol etmek önemlidir. [`Base.Checked`](@ref) modülü, taşma meydana geldiğinde hata tetikleyen taşma kontrolleri ile donatılmış bir dizi aritmetik işlem sunar. Taşmanın herhangi bir koşul altında tolere edilemeyeceği kullanım durumları için, [`BigInt`](@ref) türünü kullanmak, [Arbitrary Precision Arithmetic](@ref)'da detaylandırıldığı gibi, tavsiye edilir.

Bir taşma davranışı örneği ve bunu potansiyel olarak nasıl çözebileceğiniz aşağıdaki gibidir:

```jldoctest
julia> 10^19
-8446744073709551616

julia> big(10)^19
10000000000000000000
```

### Division errors

Tam sayı bölmesi (`div` fonksiyonu) iki istisnai duruma sahiptir: sıfıra bölme ve en düşük negatif sayıyı ([`typemin`](@ref)) -1'e bölme. Bu iki durum da [`DivideError`](@ref) hatasını fırlatır. Kalan ve modül fonksiyonları (`rem` ve `mod`), ikinci argümanı sıfır olduğunda `4d61726b646f776e2e436f64652822222c20224469766964654572726f722229_40726566` hatasını fırlatır.

## Floating-Point Numbers

Açık kayan nokta sayıları standart formatlarda temsil edilir, gerektiğinde [E-notation](https://en.wikipedia.org/wiki/Scientific_notation#E_notation) kullanılarak:

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

Yukarıdaki sonuçlar tümü [`Float64`](@ref) değerleridir. Harfi `e` yerine `f` yazarak literal [`Float32`](@ref) değerleri girilebilir:

```jldoctest
julia> x = 0.5f0
0.5f0

julia> typeof(x)
Float32

julia> 2.5f-4
0.00025f0
```

Değerler [`Float32`](@ref) kolayca dönüştürülebilir:

```jldoctest
julia> x = Float32(-1.5)
-1.5f0

julia> typeof(x)
Float32
```

Onaltı ondalık kesirli literaller de geçerlidir, ancak yalnızca [`Float64`](@ref) değerleri olarak, `p` ile ikili üssü öncesinde:

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

Yarı hassas kayan nokta sayıları da desteklenmektedir ([`Float16`](@ref)), ancak yazılımda uygulanmıştır ve hesaplamalar için [`Float32`](@ref) kullanır.

```jldoctest
julia> sizeof(Float16(4.))
2

julia> 2*Float16(4.)
Float16(8.0)
```

Alt çizgi `_` rakam ayırıcı olarak kullanılabilir:

```jldoctest
julia> 10_000, 0.000_000_005, 0xdead_beef, 0b1011_0010
(10000, 5.0e-9, 0xdeadbeef, 0xb2)
```

### Floating-point zero

Floating-point sayılar [two zeros](https://en.wikipedia.org/wiki/Signed_zero) pozitif sıfır ve negatif sıfırdır. Bunlar birbirine eşittir ancak farklı ikili temsillere sahiptir, bu [`bitstring`](@ref) fonksiyonu kullanılarak görülebilir:

```jldoctest
julia> 0.0 == -0.0
true

julia> bitstring(0.0)
"0000000000000000000000000000000000000000000000000000000000000000"

julia> bitstring(-0.0)
"1000000000000000000000000000000000000000000000000000000000000000"
```

### Special floating-point values

Gerçek sayı doğrusundaki herhangi bir noktaya karşılık gelmeyen üç belirli standart kayan nokta değeri vardır:

| `Float16` | `Float32` | `Float64` | Name              | Description                                                     |
|:--------- |:--------- |:--------- |:----------------- |:--------------------------------------------------------------- |
| `Inf16`   | `Inf32`   | `Inf`     | positive infinity | a value greater than all finite floating-point values           |
| `-Inf16`  | `-Inf32`  | `-Inf`    | negative infinity | a value less than all finite floating-point values              |
| `NaN16`   | `NaN32`   | `NaN`     | not a number      | a value not `==` to any floating-point value (including itself) |

Daha fazla tartışma için bu sonlu olmayan kayan nokta değerlerinin birbirleriyle ve diğer floatlarla nasıl sıralandığını görmek için [Numeric Comparisons](@ref) adresine bakın. [IEEE 754 standard](https://en.wikipedia.org/wiki/IEEE_754-2008) adresinde, bu kayan nokta değerleri belirli aritmetik işlemlerin sonuçlarıdır:

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

[`typemin`](@ref) ve [`typemax`](@ref) fonksiyonları ayrıca kayan nokta türlerine de uygulanır:

```jldoctest
julia> (typemin(Float16),typemax(Float16))
(-Inf16, Inf16)

julia> (typemin(Float32),typemax(Float32))
(-Inf32, Inf32)

julia> (typemin(Float64),typemax(Float64))
(-Inf, Inf)
```

### Machine epsilon

Çoğu reel sayı, kayan nokta sayılarıyla tam olarak temsil edilemez ve bu nedenle birçok amaç için, genellikle [machine epsilon](https://en.wikipedia.org/wiki/Machine_epsilon) olarak bilinen, iki bitişik temsil edilebilir kayan nokta sayısı arasındaki mesafeyi bilmek önemlidir.

Julia, [`eps`](@ref) sağlar, bu da `1.0` ile bir sonraki daha büyük temsil edilebilir kayan nokta değeri arasındaki mesafeyi verir:

```jldoctest
julia> eps(Float32)
1.1920929f-7

julia> eps(Float64)
2.220446049250313e-16

julia> eps() # same as eps(Float64)
2.220446049250313e-16
```

Bu değerler `2.0^-23` ve `2.0^-52` sırasıyla [`Float32`](@ref) ve [`Float64`](@ref) değerleridir. [`eps`](@ref) fonksiyonu ayrıca bir kayan nokta değerini argüman olarak alabilir ve bu değerin bir sonraki temsil edilebilir kayan nokta değeri ile mutlak farkını verir. Yani, `eps(x)` ifadesi, `x + eps(x)` ifadesinin `x`'den daha büyük olan bir sonraki temsil edilebilir kayan nokta değeri olduğu aynı türde bir değer döndürür:

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

İki bitişik temsil edilebilir kayan nokta sayısı arasındaki mesafe sabit değildir, ancak daha küçük değerler için daha küçüktür ve daha büyük değerler için daha büyüktür. Diğer bir deyişle, temsil edilebilir kayan nokta sayıları, sıfıra yakın gerçek sayı doğrusunda en yoğun, sıfırdan uzaklaştıkça ise üssel olarak daha seyrek hale gelir. Tanıma göre, `eps(1.0)` ile `eps(Float64)` aynı değerdir çünkü `1.0` 64 bitlik bir kayan nokta değeridir.

Julia ayrıca sırasıyla argümana en büyük veya en küçük temsil edilebilir kayan nokta sayısını döndüren [`nextfloat`](@ref) ve [`prevfloat`](@ref) fonksiyonlarını sağlar:

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

Bu örnek, bitişik temsil edilebilir kayan nokta sayıların aynı zamanda bitişik ikili tam sayı temsillerine de sahip olduğu genel ilkeyi vurgulamaktadır.

### Rounding modes

Eğer bir sayının tam bir kayan nokta temsili yoksa, uygun bir temsil edilebilir değere yuvarlanması gerekir. Ancak, bu yuvarlama işleminin nasıl yapılacağı, [IEEE 754 standard](https://en.wikipedia.org/wiki/IEEE_754-2008)'de sunulan yuvarlama modlarına göre gerektiğinde değiştirilebilir.

Varsayılan kullanılan mod her zaman [`RoundNearest`](@ref)'dır; bu, en yakın temsil edilebilir değere yuvarlar ve bağlama durumlarında en yakın değere, çift en az anlamlı bit ile yuvarlanır.

### Background and References

Kayan noktalı aritmetik, düşük seviyeli uygulama detaylarına aşina olmayan kullanıcılar için sürprizler barındıran birçok incelik içerir. Ancak, bu incelikler çoğu bilimsel hesaplama kitabında ve aşağıdaki referanslarda ayrıntılı olarak açıklanmaktadır:

  * Kesin kılavuz, kayan nokta aritmetiği için [IEEE 754-2008 Standard](https://standards.ieee.org/standard/754-2008.html); ancak, çevrimiçi olarak ücretsiz olarak mevcut değildir.
  * Kayan noktasında, kayan noktalı sayıların nasıl temsil edildiğine dair kısa ama net bir sunum için John D. Cook'un [article](https://www.johndcook.com/blog/2009/04/06/anatomy-of-a-floating-point-number/) konusundaki çalışmasına ve bu temsilin, gerçek sayıların idealize edilmiş soyutlamasından nasıl farklı davrandığına dair bazı sorunlara ilişkin [introduction](https://www.johndcook.com/blog/2009/04/06/numbers-are-a-leaky-abstraction/) çalışmasına bakmanızı öneririm.
  * Ayrıca Bruce Dawson'un [series of blog posts on floating-point numbers](https://randomascii.wordpress.com/2012/05/20/thats-not-normalthe-performance-of-odd-floats/) önerilir.
  * Mükemmel, derinlemesine bir tartışma için, kayan nokta sayıları ve bunlarla hesaplama yaparken karşılaşılan sayısal doğruluk sorunları hakkında David Goldberg'ün makalesine bakın [What Every Computer Scientist Should Know About Floating-Point Arithmetic](https://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.22.6768&rep=rep1&type=pdf).
  * Daha kapsamlı bir belge için, kayan nokta sayıların tarihi, gerekçesi ve sorunları ile birlikte sayısal hesaplama konularında birçok diğer konuyu tartışmak için [collected writings](https://people.eecs.berkeley.edu/~wkahan/) adresine bakabilirsiniz. [William Kahan](https://en.wikipedia.org/wiki/William_Kahan) olarak bilinen bu kaynak, "Kayan Noktanın Babası" olarak da anılmaktadır. Özellikle [An Interview with the Old Man of Floating-Point](https://people.eecs.berkeley.edu/~wkahan/ieee754status/754story.html) adresi ilginizi çekebilir.

## Arbitrary Precision Arithmetic

Arbitrary hassas tam sayılar ve kayan nokta sayıları ile hesaplamalara izin vermek için, Julia sırasıyla [GNU Multiple Precision Arithmetic Library (GMP)](https://gmplib.org) ve [GNU MPFR Library](https://www.mpfr.org)'i sarmalar. [`BigInt`](@ref) ve [`BigFloat`](@ref) türleri, sırasıyla Julia'da tam sayı ve kayan nokta sayıları için mevcuttur.

Konstrüktörler, bu türleri ilkel sayısal türlerden oluşturmak için vardır ve [string literal](@ref non-standard-string-literals) [`@big_str`](@ref) veya [`parse`](@ref) `AbstractString`lerden oluşturmak için kullanılabilir. `BigInt`ler, diğer yerleşik tam sayı türleri için çok büyük olduklarında tam sayı literalleri olarak da girdi olarak alınabilir. `Base` içinde işaretsiz rastgele hassasiyetli bir tam sayı türü olmadığından (`BigInt` çoğu durumda yeterlidir), onaltılık, sekizli ve ikili literaller (ondalık literallere ek olarak) kullanılabilir.

Bir kez oluşturulduktan sonra, Julia'nın [type promotion and conversion mechanism](@ref conversion-and-promotion) sayesinde tüm diğer sayısal türlerle aritmetik işlemlere katılırlar:

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

Ancak yukarıdaki ilkel türler ile [`BigInt`](@ref)/[`BigFloat`](@ref) arasında tür yükseltmesi otomatik değildir ve açıkça belirtilmelidir.

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

[`BigFloat`](@ref) işlemlerinin varsayılan hassasiyeti (anlamlı bit sayısı) ve yuvarlama modu, [`setprecision`](@ref) ve [`setrounding`](@ref) çağrılarak küresel olarak değiştirilebilir ve tüm sonraki hesaplamalar bu değişiklikleri dikkate alacaktır. Alternatif olarak, hassasiyet veya yuvarlama, belirli bir kod bloğunun yürütülmesi sırasında yalnızca aynı işlevler `do` bloğu ile kullanılarak değiştirilebilir:

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
    [`setprecision`](@ref) veya [`setrounding`](@ref) ile [`@big_str`](@ref) arasındaki ilişki, `big` dize literalleri (örneğin `big"0.3"`) için kullanılan makronun, `@big_str` bir makro olduğu gerçeği nedeniyle sezgisel olmayabilir. Ayrıntılar için `4d61726b646f776e2e436f64652822222c2022406269675f7374722229_40726566` belgelerine bakın.


## [Numeric Literal Coefficients](@id man-numeric-literal-coefficients)

Sayısal formülleri ve ifadeleri daha net hale getirmek için, Julia değişkenlerin hemen önüne bir sayısal literal yerleştirilmesine izin verir, bu da çarpımı ima eder. Bu, polinom ifadelerini yazmayı çok daha temiz hale getirir:

```jldoctest numeric-coefficients
julia> x = 3
3

julia> 2x^2 - 3x + 1
10

julia> 1.5x^2 - .5x + 1
13.0
```

Aynı zamanda üstel fonksiyonlar yazmayı daha şık hale getirir:

```jldoctest numeric-coefficients
julia> 2^2x
64
```

Sayısal sabit katsayıların önceliği, olumsuzlama gibi tekil operatörlerin önceliğinden biraz daha düşüktür. Bu nedenle `-2x` ifadesi `(-2) * x` olarak çözülür ve `√2x` ifadesi `(√2) * x` olarak çözülür. Ancak, sayısal sabit katsayılar, üstel işlemlerle birleştirildiğinde tekil operatörlerle benzer şekilde çözülür. Örneğin, `2^3x` ifadesi `2^(3x)` olarak çözülür ve `2x^3` ifadesi `2*(x^3)` olarak çözülür.

Sayısal literaller, parantezli ifadelerin katsayıları olarak da çalışır:

```jldoctest numeric-coefficients
julia> 2(x-1)^2 - 3(x-1) + 1
3
```

!!! note
    Sayısal literal katsayılarının örtük çarpım için kullanılan önceliği, çarpma (`*`) ve bölme (`/`, `\` ve `//`) gibi diğer ikili operatörlerden daha yüksektir. Bu, örneğin, `1 / 2im` ifadesinin `-0.5im` eşit olduğu ve `6 // 2(2 + 1)` ifadesinin `1 // 1` eşit olduğu anlamına gelir.


Ayrıca, parantez içindeki ifadeler değişkenlere katsayı olarak kullanılabilir ve bu, ifadenin değişkenle çarpılmasını ima eder:

```jldoctest numeric-coefficients
julia> (x-1)x
6
```

İki parantezli ifadenin yan yana getirilmesi veya bir değişkenin parantezli ifadenin önüne konulması, çarpımı ima etmek için kullanılamaz:

```jldoctest numeric-coefficients
julia> (x-1)(x+1)
ERROR: MethodError: objects of type Int64 are not callable

julia> x(x+1)
ERROR: MethodError: objects of type Int64 are not callable
```

Her iki ifade de fonksiyon uygulaması olarak yorumlanır: sayısal bir literal olmayan herhangi bir ifade, hemen ardından bir parantez geldiğinde, parantez içindeki değerlere uygulanan bir fonksiyon olarak yorumlanır (fonksiyonlar hakkında daha fazla bilgi için [Functions](@ref)'ya bakın). Bu nedenle, bu iki durumda da, sol taraftaki değer bir fonksiyon olmadığından bir hata meydana gelir.

Yukarıdaki sözdizimsel iyileştirmeler, yaygın matematiksel formüller yazarken oluşan görsel gürültüyü önemli ölçüde azaltır. Sayısal bir sabit katsayı ile çarptığı tanımlayıcı veya parantez içindeki ifade arasında boşluk olmaması gerektiğini unutmayın.

### Syntax Conflicts

Yan yana yerleştirilmiş literal katsayı sözdizimi, bazı sayısal literal sözdizimleriyle çelişebilir: onaltılık, sekizlik ve ikilik tam sayı literal'leri ile kayan noktalı literal'ler için mühendislik notasyonu. İşte sözdizimsel çelişkilerin ortaya çıktığı bazı durumlar:

  * Hexadecimal tam sayısı ifadesi `0xff`, sayısal literal `0` ile `xff` değişkeninin çarpımı olarak yorumlanabilir. Benzer belirsizlikler, `0o777` veya `0b01001010` gibi sekizli ve ikili literal ile de ortaya çıkar.
  * `1e10` kayan noktalı sayı ifadesi, sayısal literal `1`'in `e10` değişkeni ile çarpıldığı şeklinde yorumlanabilir ve benzer şekilde eşdeğer `E` biçimiyle de.
  * 32-bit kayan noktalı literal ifadesi `1.5f22`, sayısal literal `1.5`'in `f22` değişkeni ile çarpıldığı şeklinde yorumlanabilir.

Her durumda belirsizlik, sayısal literaller olarak yorumlanması lehine çözülür:

  * `0x`/`0o`/`0b` ile başlayan ifadeler her zaman onaltılık/sekizli/ikilik sayısal değerlerdir.
  * Sayısal bir literal ile başlayıp `e` veya `E` ile devam eden ifadeler her zaman kayan nokta literalleri olarak kabul edilir.
  * Sayısal bir literal ile başlayıp `f` ile biten ifadeler her zaman 32-bit kayan nokta literalleri olarak kabul edilir.

`E` ile tarihsel nedenlerden dolayı sayısal literallerde `e` ile eşdeğer olmasına karşın, `F` sadece başka bir harf olup sayısal literallerde `f` gibi davranmaz. Bu nedenle, bir sayısal literal ile başlayıp ardından `F` gelen ifadeler, sayısal literalin bir değişkenle çarpımı olarak yorumlanır; bu da demektir ki, örneğin `1.5F22`, `1.5 * F22` ile eşittir.

## Literal zero and one

Julia, belirli bir tür veya verilen bir değişkenin türü ile ilişkili olarak, literal 0 ve 1 döndüren fonksiyonlar sağlar.

| Function          | Description                                      |
|:----------------- |:------------------------------------------------ |
| [`zero(x)`](@ref) | Literal zero of type `x` or type of variable `x` |
| [`one(x)`](@ref)  | Literal one of type `x` or type of variable `x`  |

Bu fonksiyonlar, gereksiz [type conversion](@ref conversion-and-promotion) yükünden kaçınmak için [Numeric Comparisons](@ref) içinde faydalıdır.

Örnekler:

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
