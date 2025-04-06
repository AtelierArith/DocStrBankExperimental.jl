# [Variables](@id man-variables)

Bir değişken, Julia'da bir değere bağlı (veya bağlanmış) bir isimdir. Daha sonra kullanmak üzere bir değeri (örneğin, bazı matematiksel işlemlerden sonra elde ettiğiniz bir değeri) saklamak istediğinizde faydalıdır. Örneğin:

```julia-repl
# Assign the value 10 to the variable x
julia> x = 10
10

# Doing math with x's value
julia> x + 1
11

# Reassign x's value
julia> x = 1 + 1
2

# You can assign values of other types, like strings of text
julia> x = "Hello World!"
"Hello World!"
```

Julia, değişken adları için son derece esnek bir sistem sunar. Değişken adları büyük/küçük harf duyarlıdır ve anlamsal bir anlamı yoktur (yani, dil değişkenleri adlarına göre farklı şekilde ele almaz).

```jldoctest
julia> x = 1.0
1.0

julia> y = -3
-3

julia> Z = "My string"
"My string"

julia> customary_phrase = "Hello world!"
"Hello world!"

julia> UniversalDeclarationOfHumanRightsStart = "人人生而自由，在尊严和权利上一律平等。"
"人人生而自由，在尊严和权利上一律平等。"
```

Unicode adları (UTF-8 kodlamasında) izin verilir:

```jldoctest
julia> δ = 0.00001
1.0e-5

julia> 안녕하세요 = "Hello"
"Hello"
```

Julia REPL ve diğer birçok Julia düzenleme ortamında, birçok Unicode matematik sembolünü, ters eğik çizgi ile başlayan LaTeX sembol adını yazıp ardından tab tuşuna basarak yazabilirsiniz. Örneğin, `δ` değişken adı `\delta`-*tab* yazarak veya `α̂⁽²⁾` için `\alpha`-*tab*-`\hat`-*tab*-`\^(2)`-*tab* yazarak girilebilir. (Bir yerde, örneğin başkasının kodunda, nasıl yazılacağını bilmediğiniz bir sembol bulursanız, REPL yardımı size bilgi verecektir: sadece `?` yazın ve ardından sembolü yapıştırın.)

Julia, mevcut dışa aktarılan sabitleri ve fonksiyonları yerel olanlarla gölgelemenize bile izin verir (ancak bu, olası karışıklıkları önlemek için önerilmez):

```jldoctest; filter = r"with \d+ methods"
julia> pi = 3
3

julia> pi
3

julia> sqrt = 4
4

julia> length() = 5
length (generic function with 1 method)

julia> Base.length
length (generic function with 79 methods)
```

Ancak, zaten kullanılan bir yerleşik sabiti veya işlevi yeniden tanımlamaya çalışırsanız, Julia size bir hata verecektir:

```jldoctest
julia> pi
π = 3.1415926535897...

julia> pi = 3
ERROR: cannot assign a value to imported variable Base.pi from module Main

julia> sqrt(100)
10.0

julia> sqrt = 4
ERROR: cannot assign a value to imported variable Base.sqrt from module Main
```

## [Allowed Variable Names](@id man-allowed-variable-names)

Değişken adları bir harfle (A-Z veya a-z), alt çizgi ile veya 00A0'dan büyük bir Unicode kod noktası alt kümesi ile başlamalıdır; özellikle, [Unicode character categories](https://www.fileformat.info/info/unicode/category/index.htm) Lu/Ll/Lt/Lm/Lo/Nl (harfler), Sc/So (para birimi ve diğer semboller) ve birkaç diğer harf benzeri karakter (örneğin, Sm matematik sembollerinin bir alt kümesi) izin verilmektedir. Sonraki karakterler ayrıca ! ve rakamlar (0-9 ve Nd/No kategorilerindeki diğer karakterler) ile birlikte, diakritikler ve diğer modifiye edici işaretler (Mn/Mc/Me/Sk kategorileri), bazı noktalama bağlayıcıları (Pc kategorisi), primler ve birkaç diğer karakteri de içerebilir.

Operatörler `+` gibi geçerli tanımlayıcılardır, ancak özel olarak ayrıştırılırlar. Bazı bağlamlarda, operatörler değişkenler gibi kullanılabilir; örneğin, `(+)` toplama fonksiyonunu ifade eder ve `(+) = f` ile yeniden atanabilir. Unicode infiks operatörlerinin çoğu (Sm kategorisinde), `⊕` gibi, infiks operatörler olarak ayrıştırılır ve kullanıcı tanımlı yöntemler için kullanılabilir (örneğin, `const ⊗ = kron` kullanarak `⊗`'yi infiks Kronecker çarpımı olarak tanımlayabilirsiniz). Operatörler ayrıca, değiştirme işaretleri, primler ve alt/üst simgelerle sonlandırılabilir; örneğin, `+̂ₐ″` infiks bir operatör olarak `+` ile aynı önceliğe sahip olarak ayrıştırılır. Bir alt simge/üst simge harfi ile biten bir operatör ile sonraki bir değişken adı arasında bir boşluk gereklidir. Örneğin, `+ᵃ` bir operatörse, `+ᵃx` ifadesi `+ᵃ x` olarak yazılmalıdır; aksi takdirde `+ ᵃx` ifadesinde `ᵃx` değişken adı olarak değerlendirilir.

Belirli bir değişken adı sınıfı yalnızca alt çizgiler içerenlerdir. Bu tanımlayıcılar yalnızca yazma amaçlıdır. Yani, yalnızca değer ataması yapılabilir, bu değerler hemen atılır ve bu değerler herhangi bir şekilde kullanılamaz.

```julia-repl
julia> x, ___ = size([2 2; 1 1])
(2, 2)

julia> y = ___
ERROR: syntax: all-underscore identifiers are write-only and their values cannot be used in expressions

julia> println(___)
ERROR: syntax: all-underscore identifiers are write-only and their values cannot be used in expressions
```

The only explicitly disallowed names for variables are the names of the built-in [Keywords](@ref Keywords):

```julia-repl
julia> else = false
ERROR: syntax: unexpected "else"

julia> try = "No"
ERROR: syntax: unexpected "="
```

Bazı Unicode karakterleri, tanımlayıcılarda eşdeğer olarak kabul edilir. Unicode birleştirici karakterlerin (örneğin, aksanlar) farklı yollarla girilmesi eşdeğer olarak değerlendirilir (özellikle, Julia tanımlayıcıları [NFC](https://en.wikipedia.org/wiki/Unicode_equivalence) şeklindedir). Julia, görsel olarak benzer olan ve bazı giriş yöntemleriyle kolayca girilebilen birkaç standart dışı eşdeğer de içerir. Unicode karakterleri `ɛ` (U+025B: Latin küçük açık e harfi) ve `µ` (U+00B5: mikro işareti), karşılık gelen Yunan harfleri ile eşdeğer olarak kabul edilir. Orta nokta `·` (U+00B7) ve Yunan [interpunct](https://en.wikipedia.org/wiki/Interpunct) `·` (U+0387) her ikisi de matematiksel nokta operatörü `⋅` (U+22C5) olarak değerlendirilir. Eksi işareti `−` (U+2212), eksi işareti `-` (U+002D) ile eşdeğer olarak kabul edilir.

## [Assignment expressions and assignment versus mutation](@id man-assignment-expressions)

Bir atama `değişken = değer` adı `değişken`i sağ taraftaki hesaplanan `değer`e "bağlar" ve Julia tarafından tüm atama, sağ taraftaki `değer` ile eşit bir ifade olarak değerlendirilir. Bu, atamaların *zincirlenebileceği* (aynı `değer`in birden fazla değişkene atanmasıyla `değişken1 = değişken2 = değer`) veya diğer ifadelerde kullanılabileceği anlamına gelir ve bu nedenle sonuçları REPL'de sağ tarafın değeri olarak gösterilir. (Genel olarak, REPL, değerlendirdiğiniz her ifadenin değerini gösterir.) Örneğin, burada `b = 2+2` ifadesinin değeri `4`, başka bir aritmetik işlem ve atamada kullanılır:

```jldoctest
julia> a = (b = 2+2) + 3
7

julia> a
7

julia> b
4
```

Yaygın bir karışıklık, *atama* (bir değere yeni bir "isim" verme) ile *değiştirme* (bir değeri değiştirme) arasındaki ayrımdır. Eğer `a = 2` komutunu çalıştırıp ardından `a = 3` komutunu çalıştırırsanız, "isim" `a`yı yeni bir değer olan `3`'e referans verecek şekilde değiştirmiş olursunuz... `2` sayısını değiştirmediniz, bu yüzden `2+2` hâlâ `4` verecek ve `6` vermeyecek! Bu ayrım, içeriği *değiştirilebilen* türlerle, örneğin [arrays](@ref lib-arrays), çalışırken daha net hale gelir:

```jldoctest mutation_vs_rebind
julia> a = [1,2,3] # an array of 3 integers
3-element Vector{Int64}:
 1
 2
 3

julia> b = a   # both b and a are names for the same array!
3-element Vector{Int64}:
 1
 2
 3
```

Burada, `b = a` satırı *kopya* oluşturmaz, sadece `b` adını *aynı* dizi `a`'ya bağlar: hem `b` hem de `a` bellekteki bir diziye `[1,2,3]` "işaret eder". Buna karşılık, bir atama `a[i] = value` *içeriği* *değiştirir* ve değiştirilen dizi hem `a` hem de `b` adları aracılığıyla görünür hale gelir:

```jldoctest mutation_vs_rebind
julia> a[1] = 42     # change the first element
42

julia> a = 3.14159   # a is now the name of a different object
3.14159

julia> b   # b refers to the original array object, which has been mutated
3-element Vector{Int64}:
 42
  2
  3
```

Yani, `a[i] = value` (bir takma ad [`setindex!`](@ref) için) mevcut bir dizi nesnesini bellekte *değiştirir*, `a` veya `b` aracılığıyla erişilebilir. Sonrasında `a = 3.14159` ayarlamak bu diziyi değiştirmez, sadece `a`yı farklı bir nesneye bağlar; dizi hala `b` aracılığıyla erişilebilir. Mevcut bir nesneyi değiştirmek için başka bir yaygın sözdizimi `a.field = value` (bir takma ad [`setproperty!`](@ref) için) olup, bir [`mutable struct`](@ref) değiştirmek için kullanılabilir. Ayrıca, nokta ataması ile değişim de vardır, örneğin `b .= 5:7` (bu, dizimizi `b`'yi yerinde `[5,6,7]` içerecek şekilde değiştirir), Julia'nın [vectorized "dot" syntax](@ref man-dot-operators)'ün bir parçasıdır.

When you call a [function](@ref man-functions) in Julia, it behaves as if you *assigned* the argument values to new variable names corresponding to the function arguments, as discussed in [Argument-Passing Behavior](@ref man-argument-passing).  (By [convention](@ref man-punctuation), functions that mutate one or more of their arguments have names ending with `!`.)

## Stylistic Conventions

Julia, geçerli isimler üzerinde çok az kısıtlama getirse de, aşağıdaki gelenekleri benimsemek faydalı olmuştur:

  * değişkenlerin isimleri küçük harfle yazılmıştır.
  * Kelime ayrımı alt çizgilerle (`'_'`) belirtilebilir, ancak alt çizgi kullanımı, isim aksi takdirde okunması zor olursa dışında önerilmez.
  * `Type` ve `Module` isimleri büyük harfle başlar ve kelime ayrımı alt çizgi yerine büyük camel case ile gösterilir.
  * `function` ve `macro` isimleri alt çizgi olmadan küçük harfle yazılmalıdır.
  * Argümanlarına yazan fonksiyonların isimleri `!` ile biter. Bunlar bazen "değiştiren" veya "yerinde" fonksiyonlar olarak adlandırılır çünkü çağrıldıktan sonra argümanlarında değişiklikler üretmek için tasarlanmışlardır, sadece bir değer döndürmek için değil.

Daha fazla bilgi için stilistik gelenekler hakkında [Style Guide](@ref)'ya bakın.
