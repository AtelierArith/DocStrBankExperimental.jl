# [Strings](@id man-strings)

Dizeler, karakterlerin sonlu dizileridir. Elbette, gerçek sorun, bir karakterin ne olduğunu sorduğunuzda gelir. İngilizce konuşanların aşina olduğu karakterler `A`, `B`, `C` gibi harflerdir; bunlara sayılar ve yaygın noktalama işaretleri de dahildir. Bu karakterler, [ASCII](https://en.wikipedia.org/wiki/ASCII) standardı tarafından 0 ile 127 arasındaki tam sayı değerlerine eşleştirilerek standartlaştırılmıştır. Elbette, aksanlar ve diğer modifikasyonlarla birlikte ASCII karakterlerinin varyantları, Kiril ve Yunan gibi ilgili yazı sistemleri ve Arapça, Çince, İbranice, Hintçe, Japonca ve Korece gibi ASCII ve İngilizce ile tamamen alakasız yazı sistemleri de dahil olmak üzere, diğer birçok karakter de vardır. [Unicode](https://en.wikipedia.org/wiki/Unicode) standardı, bir karakterin tam olarak ne olduğunu ele alan karmaşıklıkları ele alır ve bu sorunu ele alan kesin standart olarak genel olarak kabul edilir. İhtiyaçlarınıza bağlı olarak, bu karmaşıklıkları tamamen göz ardı edebilir ve yalnızca ASCII karakterlerinin var olduğunu varsayabilirsiniz veya karşılaşabileceğiniz herhangi bir karakter veya kodlamayı işleyebilen kod yazabilirsiniz. Julia, düz ASCII metni ile çalışmayı basit ve verimli hale getirir ve Unicode ile çalışmak da mümkün olduğunca basit ve verimlidir. Özellikle, ASCII dizelerini işlemek için C tarzı dize kodu yazabilirsiniz ve bu kodlar, hem performans hem de anlam açısından beklendiği gibi çalışacaktır. Eğer böyle bir kod, ASCII dışı metinle karşılaşırsa, sessizce bozuk sonuçlar sunmak yerine, net bir hata mesajıyla nazikçe başarısız olacaktır. Bu olduğunda, ASCII dışı verileri işlemek için kodu değiştirmek oldukça basittir.

Julia'nın dizeleri hakkında birkaç dikkate değer yüksek düzey özellik bulunmaktadır:

  * Julia'da dizeler (ve dize literalleri) için kullanılan yerleşik somut tür [`String`](@ref)'dır. Bu, [Unicode](https://en.wikipedia.org/wiki/Unicode) karakterlerinin tam aralığını destekler ve [UTF-8](https://en.wikipedia.org/wiki/UTF-8) kodlaması aracılığıyla yapılır. (Diğer Unicode kodlamalarına dönüştürmek için [`transcode`](@ref) fonksiyonu sağlanmıştır.)
  * Tüm dize türleri, `AbstractString` soyut türünün alt türleridir ve harici paketler ek `AbstractString` alt türleri tanımlar (örneğin, diğer kodlamalar için). Bir dize argümanı bekleyen bir fonksiyon tanımlarsanız, herhangi bir dize türünü kabul etmek için türü `AbstractString` olarak belirtmelisiniz.
  * C ve Java gibi, ancak çoğu dinamik dilden farklı olarak, Julia'nın [`AbstractChar`](@ref) olarak adlandırılan tek bir karakteri temsil etmek için birinci sınıf bir türü vardır. Yerleşik [`Char`](@ref) alt türü, herhangi bir Unicode karakterini temsil edebilen 32 bitlik bir ilkel türdür (ve UTF-8 kodlamasına dayanmaktadır).
  * Java'da olduğu gibi, dizeler değiştirilemez: bir `AbstractString` nesnesinin değeri değiştirilemez. Farklı bir dize değeri oluşturmak için, diğer dizelerin parçalarından yeni bir dize oluşturursunuz.
  * Kavram olarak, bir dize, indekslerden karakterlere *kısmi bir fonksiyon* olarak tanımlanır: bazı indeks değerleri için, hiçbir karakter değeri döndürülmez ve bunun yerine bir istisna fırlatılır. Bu, Unicode dizelerinin değişken genişlikteki kodlamaları için hem verimli hem de basit bir şekilde uygulanamayacak olan karakter indeksine göre değil, kodlanmış bir temsilin bayt indeksi ile dizelere verimli bir şekilde erişim sağlamaya olanak tanır.

## [Characters](@id man-characters)

Bir `Char` değeri tek bir karakteri temsil eder: bu, özel bir literal temsili ve uygun aritmetik davranışları olan 32 bitlik bir ilkel türdür ve [Unicode code point](https://en.wikipedia.org/wiki/Code_point) temsil eden bir sayısal değere dönüştürülebilir. (Julia paketleri, diğer [text encodings](https://en.wikipedia.org/wiki/Character_encoding) için işlemleri optimize etmek üzere `AbstractChar`'ın diğer alt türlerini tanımlayabilir.) İşte `Char` değerlerinin nasıl girileceği ve gösterileceği (karakter literal'lerinin tek tırnak ile sınırlı olduğunu, çift tırnak ile değil, unutmayın):

```jldoctest
julia> c = 'x'
'x': ASCII/Unicode U+0078 (category Ll: Letter, lowercase)

julia> typeof(c)
Char
```

Bir `Char`'ı kolayca tam sayı değerine, yani kod noktasına dönüştürebilirsiniz:

```jldoctest
julia> c = Int('x')
120

julia> typeof(c)
Int64
```

32-bit mimarilerde, [`typeof(c)`](@ref) [`Int32`](@ref) olacaktır. Bir tam sayı değerini `Char`'a geri dönüştürmek de aynı derecede kolaydır:

```jldoctest
julia> Char(120)
'x': ASCII/Unicode U+0078 (category Ll: Letter, lowercase)
```

Tüm tam sayı değerleri geçerli Unicode kod noktaları değildir, ancak performans için `Char` dönüşümü her karakter değerinin geçerli olup olmadığını kontrol etmez. Her dönüştürülen değerin geçerli bir kod noktası olup olmadığını kontrol etmek istiyorsanız, [`isvalid`](@ref) fonksiyonunu kullanın:

```jldoctest
julia> Char(0x110000)
'\U110000': Unicode U+110000 (category In: Invalid, too high)

julia> isvalid(Char, 0x110000)
false
```

Bu yazı itibarıyla, geçerli Unicode kod noktaları `U+0000` ile `U+D7FF` ve `U+E000` ile `U+10FFFF` arasındadır. Bunların hepsi henüz anlaşılır anlamlar atanmamış olabilir veya uygulamalar tarafından mutlaka yorumlanabilir değildir, ancak bu değerlerin tamamı geçerli Unicode karakterleri olarak kabul edilmektedir.

Tek bir karakteri `\u` ile ardından dört onaltılık basamak veya `\U` ile ardından sekiz onaltılık basamak yazarak tek tırnak içinde girebilirsiniz (en uzun geçerli değer yalnızca altı basamak gerektirir):

```jldoctest
julia> '\u0'
'\0': ASCII/Unicode U+0000 (category Cc: Other, control)

julia> '\u78'
'x': ASCII/Unicode U+0078 (category Ll: Letter, lowercase)

julia> '\u2200'
'∀': Unicode U+2200 (category Sm: Symbol, math)

julia> '\U10ffff'
'\U10ffff': Unicode U+10FFFF (category Cn: Other, not assigned)
```

Julia sisteminizin yerel ayarlarını ve dil ayarlarını kullanarak hangi karakterlerin olduğu gibi yazılabileceğini ve hangilerinin genel, kaçış `\u` veya `\U` girdi biçimleriyle çıktılanması gerektiğini belirler. Bu Unicode kaçış biçimlerine ek olarak, [C's traditional escaped input forms](https://en.wikipedia.org/wiki/C_syntax#Backslash_escapes) de kullanılabilir:

```jldoctest
julia> Int('\0')
0

julia> Int('\t')
9

julia> Int('\n')
10

julia> Int('\e')
27

julia> Int('\x7f')
127

julia> Int('\177')
127
```

`Char` değerleri ile karşılaştırmalar ve sınırlı miktarda aritmetik işlemler yapabilirsiniz:

```jldoctest
julia> 'A' < 'a'
true

julia> 'A' <= 'a' <= 'Z'
false

julia> 'A' <= 'X' <= 'Z'
true

julia> 'x' - 'a'
23

julia> 'A' + 1
'B': ASCII/Unicode U+0042 (category Lu: Letter, uppercase)
```

## String Basics

Dize dizeleri çift tırnak veya üçlü çift tırnak ile sınırlıdır (tek tırnak ile değil):

```jldoctest helloworldstring
julia> str = "Hello, world.\n"
"Hello, world.\n"

julia> """Contains "quote" characters"""
"Contains \"quote\" characters"
```

Uzun satırlar, yeni satırdan önce bir ters eğik çizgi (`\`) ile bölünebilir:

```jldoctest
julia> "This is a long \
       line"
"This is a long line"
```

Bir dizeden bir karakter çıkarmak istiyorsanız, ona indeksle erişirsiniz:

```jldoctest helloworldstring
julia> str[begin]
'H': ASCII/Unicode U+0048 (category Lu: Letter, uppercase)

julia> str[1]
'H': ASCII/Unicode U+0048 (category Lu: Letter, uppercase)

julia> str[6]
',': ASCII/Unicode U+002C (category Po: Punctuation, other)

julia> str[end]
'\n': ASCII/Unicode U+000A (category Cc: Other, control)
```

Birçok Julia nesnesi, dizeler de dahil olmak üzere, tam sayılarla indekslenebilir. İlk elemanın (bir dizenin ilk karakteri) indeksi [`firstindex(str)`](@ref) ile döndürülür ve son elemanın (karakterin) indeksi [`lastindex(str)`](@ref) ile döndürülür. `begin` ve `end` anahtar kelimeleri, belirtilen boyut boyunca ilk ve son indeksler için kısayol olarak bir indeksleme işlemi içinde kullanılabilir. Dize indekslemesi, Julia'daki çoğu indeksleme gibi 1 tabanlıdır: `firstindex` her `AbstractString` için her zaman `1` döndürür. Ancak aşağıda göreceğimiz gibi, `lastindex(str)` genel olarak bir dize için `length(str)` ile aynı değildir, çünkü bazı Unicode karakterleri birden fazla "kod birimi" kaplayabilir.

[`end`](@ref) ile normal bir değer gibi aritmetik ve diğer işlemleri gerçekleştirebilirsiniz:

```jldoctest helloworldstring
julia> str[end-1]
'.': ASCII/Unicode U+002E (category Po: Punctuation, other)

julia> str[end÷2]
' ': ASCII/Unicode U+0020 (category Zs: Separator, space)
```

`begin` (`1`) veya `end`'den büyük bir indeks kullanmak bir hata oluşturur:

```jldoctest helloworldstring
julia> str[begin-1]
ERROR: BoundsError: attempt to access 14-codeunit String at index [0]
[...]

julia> str[end+1]
ERROR: BoundsError: attempt to access 14-codeunit String at index [15]
[...]
```

Bir alt dizeyi aralık dizinleme kullanarak da çıkarabilirsiniz:

```jldoctest helloworldstring
julia> str[4:9]
"lo, wo"
```

`str[k]` ve `str[k:k]` ifadelerinin aynı sonucu vermediğine dikkat edin:

```jldoctest helloworldstring
julia> str[6]
',': ASCII/Unicode U+002C (category Po: Punctuation, other)

julia> str[6:6]
","
```

Öncelikle, ilki `Char` türünde tek bir karakter değeridir, ikincisi ise yalnızca tek bir karakter içeren bir dize değeridir. Julia'da bunlar çok farklı şeylerdir.

Aralık dizinleme, orijinal dizenin seçilen kısmının bir kopyasını oluşturur. Alternatif olarak, [`SubString`](@ref) türünü kullanarak bir dizenin içine bir görünüm oluşturmak mümkündür. Daha basit bir şekilde, bir kod bloğu üzerinde [`@views`](@ref) makrosunu kullanmak, tüm dize dilimlerini alt dizelere dönüştürür. Örneğin:

```jldoctest
julia> str = "long string"
"long string"

julia> substr = SubString(str, 1, 4)
"long"

julia> typeof(substr)
SubString{String}

julia> @views typeof(str[1:4]) # @views converts slices to SubStrings
SubString{String}
```

Birçok standart fonksiyon, [`chop`](@ref), [`chomp`](@ref) veya [`strip`](@ref) gibi, [`SubString`](@ref) döndürmektedir.

## Unicode and UTF-8

Julia tamamen Unicode karakterlerini ve dizelerini destekler. [discussed above](@ref man-characters) olarak, karakter literallerinde, Unicode kod noktaları Unicode `\u` ve `\U` kaçış dizileri kullanılarak temsil edilebilir, ayrıca tüm standart C kaçış dizileri de kullanılabilir. Bunlar aynı şekilde dize literalleri yazmak için de kullanılabilir:

```jldoctest unicodestring
julia> s = "\u2200 x \u2203 y"
"∀ x ∃ y"
```

Bu Unicode karakterlerinin kaçış olarak mı yoksa özel karakterler olarak mı görüntüleneceği, terminalinizin yerel ayarlarına ve Unicode desteğine bağlıdır. Dize literalleri UTF-8 kodlaması kullanılarak kodlanır. UTF-8, değişken genişlikte bir kodlama olup, tüm karakterlerin aynı sayıda bayt ("kod birimi") ile kodlanmadığı anlamına gelir. UTF-8'de, ASCII karakterleri — yani 0x80 (128) altındaki kod noktalarına sahip olanlar — ASCII'de olduğu gibi tek bir bayt kullanılarak kodlanırken, 0x80 ve üzerindeki kod noktaları birden fazla bayt kullanılarak kodlanır — karakter başına en fazla dört bayt.

Julia'da dize indeksleri, rastgele karakterleri (kod noktaları) kodlamak için kullanılan sabit genişlikteki yapı taşları olan kod birimlerine (= UTF-8 için baytlara) atıfta bulunur. Bu, bir `String` içindeki her indeksin mutlaka bir karakter için geçerli bir indeks olmadığı anlamına gelir. Geçersiz bir bayt indeksinde bir dizeye indeksleme yaparsanız, bir hata fırlatılır:

```jldoctest unicodestring
julia> s[1]
'∀': Unicode U+2200 (category Sm: Symbol, math)

julia> s[2]
ERROR: StringIndexError: invalid index [2], valid nearby indices [1]=>'∀', [4]=>' '
Stacktrace:
[...]

julia> s[3]
ERROR: StringIndexError: invalid index [3], valid nearby indices [1]=>'∀', [4]=>' '
Stacktrace:
[...]

julia> s[4]
' ': ASCII/Unicode U+0020 (category Zs: Separator, space)
```

Bu durumda, `∀` karakteri üç baytlık bir karakterdir, bu nedenle 2 ve 3 indeksleri geçersizdir ve bir sonraki karakterin indeksi 4'tür; bu bir sonraki geçerli indeks [`nextind(s,1)`](@ref) ile hesaplanabilir ve ondan sonraki indeks `nextind(s,4)` ile hesaplanabilir ve bu şekilde devam eder.

`end` her zaman bir koleksiyondaki son geçerli indeksi temsil ettiğinden, `end-1` sondan bir önceki karakter çok baytlıysa geçersiz bir bayt indeksini referans alır.

```jldoctest unicodestring
julia> s[end-1]
' ': ASCII/Unicode U+0020 (category Zs: Separator, space)

julia> s[end-2]
ERROR: StringIndexError: invalid index [9], valid nearby indices [7]=>'∃', [10]=>' '
Stacktrace:
[...]

julia> s[prevind(s, end, 2)]
'∃': Unicode U+2203 (category Sm: Symbol, math)
```

İlk durum çalışır, çünkü son karakter `y` ve boşluk birer baytlık karakterlerdir, oysa `end-2` `∃` çok baytlı temsilinin ortasına indekslenir. Bu durum için doğru yol `prevind(s, lastindex(s), 2)` kullanmaktır veya bu değeri `s`'ye indekslemek için `s[prevind(s, end, 2)]` yazabilirsiniz ve `end` `lastindex(s)`'ye genişler.

Bir alt dizeyi aralık dizinleme kullanarak çıkarmak, geçerli bayt dizinleri bekler veya bir hata fırlatılır:

```jldoctest unicodestring
julia> s[1:1]
"∀"

julia> s[1:2]
ERROR: StringIndexError: invalid index [2], valid nearby indices [1]=>'∀', [4]=>' '
Stacktrace:
[...]

julia> s[1:4]
"∀ "
```

Değişken uzunlukta kodlamalar nedeniyle, bir dizedeki karakter sayısı ([`length(s)`](@ref)) her zaman son indeksle aynı değildir. `1` ile [`lastindex(s)`](@ref) arasındaki indekslerde yineleme yaparsanız ve `s`'ye indeksleme yaparsanız, hata fırlatılmadığında döndürülen karakter dizisi, `s` dizisini oluşturan karakterlerin dizisidir. Bu nedenle `length(s) <= lastindex(s)`'dir, çünkü bir dizideki her karakterin kendi indeksi olmalıdır. Aşağıda, `s`'nin karakterleri arasında yineleme yapmanın verimsiz ve ayrıntılı bir yolu verilmiştir:

```jldoctest unicodestring
julia> for i = firstindex(s):lastindex(s)
           try
               println(s[i])
           catch
               # ignore the index error
           end
       end
∀

x

∃

y
```

Boş satırlarda aslında boşluklar var. Neyse ki, yukarıdaki garip deyim, bir dizedeki karakterler arasında yinelemek için gereksizdir, çünkü dizeyi bir yineleyici nesne olarak kullanabilirsiniz, istisna işleme gerektirmez:

```jldoctest unicodestring
julia> for c in s
           println(c)
       end
∀

x

∃

y
```

Eğer bir dize için geçerli indeksler elde etmeniz gerekiyorsa, yukarıda bahsedilen [`nextind`](@ref) ve [`prevind`](@ref) fonksiyonlarını bir sonraki/geçerli indekse artırmak/azaltmak için kullanabilirsiniz. Ayrıca geçerli karakter indeksleri üzerinde yinelemek için [`eachindex`](@ref) fonksiyonunu da kullanabilirsiniz:

```jldoctest unicodestring
julia> collect(eachindex(s))
7-element Vector{Int64}:
  1
  4
  5
  6
  7
 10
 11
```

Ham hamur kod birimlerine (UTF-8 için baytlar) erişmek için [`codeunit(s,i)`](@ref) fonksiyonunu kullanabilirsiniz; burada `i` indeksi `1`'den [`ncodeunits(s)`](@ref)'ya kadar ardışık olarak çalışır. [`codeunits(s)`](@ref) fonksiyonu, bu ham kod birimlerine (baytlar) bir dizi olarak erişmenizi sağlayan bir `AbstractVector{UInt8}` sarmalayıcı döndürür.

Julia'daki dizeler geçersiz UTF-8 kod birimi dizileri içerebilir. Bu kural, herhangi bir bayt dizisini `String` olarak ele almayı sağlar. Bu tür durumlarda, soldan sağa bir kod birimi dizisini ayrıştırırken, karakterler aşağıdaki bit desenlerinden birinin başlangıcına uyan en uzun 8 bitlik kod birimi dizisi ile oluşturulur (her `x` `0` veya `1` olabilir):

  * `0xxxxxxx`;
  * `110xxxxx` `10xxxxxx`;
  * `1110xxxx` `10xxxxxx` `10xxxxxx`;
  * `11110xxx` `10xxxxxx` `10xxxxxx` `10xxxxxx`;
  * `10xxxxxx`;
  * `11111xxx`.

Özellikle bu, aşırı uzun ve çok yüksek kod birimi dizilerinin ve bunların ön eklerinin tek bir geçersiz karakter olarak, birden fazla geçersiz karakter olarak değil, ele alındığı anlamına gelir. Bu kural en iyi bir örnekle açıklanabilir:

```julia-repl
julia> s = "\xc0\xa0\xe2\x88\xe2|"
"\xc0\xa0\xe2\x88\xe2|"

julia> foreach(display, s)
'\xc0\xa0': [overlong] ASCII/Unicode U+0020 (category Zs: Separator, space)
'\xe2\x88': Malformed UTF-8 (category Ma: Malformed, bad data)
'\xe2': Malformed UTF-8 (category Ma: Malformed, bad data)
'|': ASCII/Unicode U+007C (category Sm: Symbol, math)

julia> isvalid.(collect(s))
4-element BitArray{1}:
 0
 0
 0
 1

julia> s2 = "\xf7\xbf\xbf\xbf"
"\U1fffff"

julia> foreach(display, s2)
'\U1fffff': Unicode U+1FFFFF (category In: Invalid, too high)
```

İlk iki kod biriminin `s` dizesinde boşluk karakterinin aşırı uzun bir kodlamasını oluşturduğunu görebiliriz. Geçersizdir, ancak bir dize içinde tek bir karakter olarak kabul edilir. Sonraki iki kod birimi, üç baytlık bir UTF-8 dizisinin geçerli başlangıcını oluşturur. Ancak, beşinci kod birimi `\xe2` onun geçerli devamı değildir. Bu nedenle, kod birimleri 3 ve 4 de bu dizede bozuk karakterler olarak yorumlanır. Benzer şekilde, kod birimi 5, `|` onun için geçerli bir devam olmadığı için bozuk bir karakter oluşturur. Son olarak, `s2` dizesi bir kod noktasının çok yüksek olduğunu içerir.

Julia varsayılan olarak UTF-8 kodlamasını kullanır ve yeni kodlamalar için destek paketler aracılığıyla eklenebilir. Örneğin, [LegacyStrings.jl](https://github.com/JuliaStrings/LegacyStrings.jl) paketi `UTF16String` ve `UTF32String` türlerini uygular. Diğer kodlamalar ve bunlar için destek sağlama yöntemleri ile ilgili ek tartışmalar, bu belgenin kapsamının ötesindedir. UTF-8 kodlama sorunları hakkında daha fazla tartışma için, aşağıdaki [byte array literals](@ref man-byte-array-literals) bölümüne bakın. [`transcode`](@ref) fonksiyonu, çeşitli UTF-xx kodlamaları arasında veri dönüştürmek için sağlanmıştır, esasen dış veriler ve kütüphanelerle çalışmak için.

## [Concatenation](@id man-concatenation)

En yaygın ve faydalı dize işlemlerinden biri birleştirmedir:

```jldoctest stringconcat
julia> greet = "Hello"
"Hello"

julia> whom = "world"
"world"

julia> string(greet, ", ", whom, ".\n")
"Hello, world.\n"
```

Potansiyel tehlikeli durumların, geçersiz UTF-8 dizelerinin birleştirilmesi gibi, farkında olmak önemlidir. Ortaya çıkan dize, giriş dizelerinden farklı karakterler içerebilir ve karakter sayısı birleştirilen dizelerin karakter sayılarının toplamından daha az olabilir, örneğin:

```julia-repl
julia> a, b = "\xe2\x88", "\x80"
("\xe2\x88", "\x80")

julia> c = string(a, b)
"∀"

julia> collect.([a, b, c])
3-element Vector{Vector{Char}}:
 ['\xe2\x88']
 ['\x80']
 ['∀']

julia> length.([a, b, c])
3-element Vector{Int64}:
 1
 1
 1
```

Bu durum yalnızca geçersiz UTF-8 dizeleri için meydana gelebilir. Geçerli UTF-8 dizeleri için birleştirme, dizelerdeki tüm karakterleri korur ve dize uzunluklarının toplamsallığını sağlar.

Julia ayrıca string birleştirme için [`*`](@ref) sağlar:

```jldoctest stringconcat
julia> greet * ", " * whom * ".\n"
"Hello, world.\n"
```

`*` kullanıcılar için şaşırtıcı bir seçim gibi görünse de, bu kullanım matematikte, özellikle soyut cebirde bir öncülüğe sahiptir.

Matematikte, `+` genellikle *komütatif* bir işlemi belirtir; burada operandların sırası önemli değildir. Bunun bir örneği, aynı şekle sahip herhangi iki matris `A` ve `B` için `A + B == B + A` olan matris toplamasıdır. Buna karşılık, `*` genellikle *komütatif olmayan* bir işlemi belirtir; burada operandların sırası *önemlidir*. Bunun bir örneği, genel olarak `A * B != B * A` olan matris çarpımıdır. Matris çarpımında olduğu gibi, dize birleştirme de komütatif değildir: `greet * whom != whom * greet`. Bu nedenle, `*` yaygın matematiksel kullanımla tutarlı olarak infiks dize birleştirme operatörü için daha doğal bir seçimdir.

More precisely, the set of all finite-length strings *S* together with the string concatenation operator `*` forms a [free monoid](https://en.wikipedia.org/wiki/Free_monoid) (*S*, `*`). The identity element of this set is the empty string, `""`. Whenever a free monoid is not commutative, the operation is typically represented as `\cdot`, `*`, or a similar symbol, rather than `+`, which as stated usually implies commutativity.

## [Interpolation](@id string-interpolation)

Dize ekleme kullanarak dizeler oluşturmak biraz zahmetli hale gelebilir. Ancak, [`string`](@ref) gibi bu ayrıntılı çağrılara olan ihtiyacı azaltmak veya tekrar eden çarpımları önlemek için, Julia `$` kullanarak dize literallerine interpolasyon yapmaya izin verir; Perl'deki gibi:

```jldoctest
julia> greet = "Hello"; whom = "world";

julia> "$greet, $whom.\n"
"Hello, world.\n"
```

Bu, yukarıdaki dize birleştirmesine göre daha okunabilir ve kullanışlıdır - sistem bu görünüşte tek dize sabitini `string(greet, ", ", whom, ".\n")` çağrısına dönüştürür.

En kısa tamamlanmış ifade `$` işareti alındıktan sonra, değeri dizeye yerleştirilecek ifade olarak kabul edilir. Böylece, herhangi bir ifadeyi parantez kullanarak bir dizeye yerleştirebilirsiniz:

```jldoctest
julia> "1 + 2 = $(1 + 2)"
"1 + 2 = 3"
```

Her iki birleştirme ve dize interpolasyonu, nesneleri dize biçimine dönüştürmek için [`string`](@ref) çağrısını yapar. Ancak, `string` aslında sadece [`print`](@ref)'nın çıktısını döndürür, bu nedenle yeni türler `4d61726b646f776e2e436f64652822222c20227072696e742229_40726566` veya [`show`](@ref)'ya yöntemler eklemelidir, `string` yerine.

Çoğu `AbstractString` olmayan nesne, literal ifadeler olarak nasıl girildiklerine yakın bir şekilde string'lere dönüştürülür:

```jldoctest
julia> v = [1,2,3]
3-element Vector{Int64}:
 1
 2
 3

julia> "v: $v"
"v: [1, 2, 3]"
```

[`string`](@ref) `AbstractString` ve `AbstractChar` değerleri için kimliktir, bu nedenle bunlar kendileri olarak, tırnaksız ve kaçışsız bir şekilde dizelere yerleştirilir:

```jldoctest
julia> c = 'x'
'x': ASCII/Unicode U+0078 (category Ll: Letter, lowercase)

julia> "hi, $c"
"hi, x"
```

Bir dize literalinde `$` karakterini dahil etmek için, onu bir ters eğik çizgi ile kaçırın:

```jldoctest
julia> print("I have \$100 in my account.\n")
I have $100 in my account.
```

## Triple-Quoted String Literals

Üçlü tırnaklar (`"""..."""`) kullanılarak oluşturulan dizeler, daha uzun metin blokları oluşturmak için yararlı olabilecek bazı özel davranışlara sahiptir.

İlk olarak, üç tırnaklı dizeler de en az girintili satırın seviyesine göre girintisizleştirilir. Bu, girintili kod içinde dizeleri tanımlamak için yararlıdır. Örneğin:

```jldoctest
julia> str = """
           Hello,
           world.
         """
"  Hello,\n  world.\n"
```

Bu durumda, kapanış `"""` öncesindeki son (boş) satır girinti seviyesini belirler.

Girintili seviye, tüm satırlardaki en uzun ortak başlangıç boşluk veya sekme dizisi olarak belirlenir; bu, açılış `"""` sonrasındaki satırları ve yalnızca boşluk veya sekme içeren satırları hariç tutar (kapanış `"""` içeren satır her zaman dahil edilir). Daha sonra, açılış `"""` sonrasındaki metin hariç tüm satırlardan, ortak başlangıç dizisi kaldırılır (bu diziyi ile başlayan yalnızca boşluk ve sekme içeren satırlar da dahil). Örneğin:

```jldoctest
julia> """    This
         is
           a test"""
"    This\nis\n  a test"
```

Sonraki olarak, eğer açılış `"""` bir yeni satır ile takip ediliyorsa, yeni satır sonuçta oluşan string'den çıkarılır.

```julia
"""hello"""
```

eşittir

```julia
"""
hello"""
```

ama

```julia
"""

hello"""
```

bir satır sonu içerir.

Satır sonu boşluğu, girintiden sonra kaldırılır. Örneğin:

```jldoctest
julia> """
         Hello,
         world."""
"Hello,\nworld."
```

Eğer yeni satır bir ters eğik çizgi ile kaldırılırsa, girinti de dikkate alınacaktır:

```jldoctest
julia> """
         Averylong\
         word"""
"Averylongword"
```

Son boşluk değiştirilmeden bırakılır.

Üçlü tırnaklı dize literalleri, `"` karakterlerini kaçırmadan içerebilir.

Not edin ki, tek veya üçlü tırnak içinde yer alan literal dizgelerde satır sonları, dizgede bir yeni satır (LF) karakteri `\n` ile sonuçlanır, editörünüz satırları sonlandırmak için bir taşıyıcı dönüş `\r` (CR) veya CRLF kombinasyonu kullanıyor olsa bile. Bir dizgede bir CR dahil etmek için, açık bir kaçış `\r` kullanın; örneğin, literal dizgeyi `"a CRLF line ending\r\n"` olarak girebilirsiniz.

## Common Operations

Dize lexikografik olarak karşılaştırmak için standart karşılaştırma operatörlerini kullanabilirsiniz:

```jldoctest
julia> "abracadabra" < "xylophone"
true

julia> "abracadabra" == "xylophone"
false

julia> "Hello, world." != "Goodbye, world."
true

julia> "1 + 2 = 3" == "1 + 2 = $(1 + 2)"
true
```

Belirli bir karakterin indeksini [`findfirst`](@ref) ve [`findlast`](@ref) fonksiyonlarını kullanarak arayabilirsiniz:

```jldoctest
julia> findfirst('o', "xylophone")
4

julia> findlast('o', "xylophone")
7

julia> findfirst('z', "xylophone")
```

Belirli bir ofsetten bir karakter aramaya [`findnext`](@ref) ve [`findprev`](@ref) fonksiyonlarını kullanarak başlayabilirsiniz:

```jldoctest
julia> findnext('o', "xylophone", 1)
4

julia> findnext('o', "xylophone", 5)
7

julia> findprev('o', "xylophone", 5)
4

julia> findnext('o', "xylophone", 8)
```

[`occursin`](@ref) fonksiyonunu bir alt dizeyi bir dizede bulup bulmadığını kontrol etmek için kullanabilirsiniz:

```jldoctest
julia> occursin("world", "Hello, world.")
true

julia> occursin("o", "Xylophon")
true

julia> occursin("a", "Xylophon")
false

julia> occursin('o', "Xylophon")
true
```

Son örnek, [`occursin`](@ref) ifadesinin bir karakter literali arayabileceğini göstermektedir.

İki başka kullanışlı dize işlevi [`repeat`](@ref) ve [`join`](@ref):

```jldoctest
julia> repeat(".:Z:.", 10)
".:Z:..:Z:..:Z:..:Z:..:Z:..:Z:..:Z:..:Z:..:Z:..:Z:."

julia> join(["apples", "bananas", "pineapples"], ", ", " and ")
"apples, bananas and pineapples"
```

Diğer bazı yararlı fonksiyonlar şunlardır:

  * [`firstindex(str)`](@ref) dizenin içine indekslemek için kullanılabilecek en küçük (bayt) indeksini verir (her zaman dizeler için 1'dir, diğer konteynerler için bu geçerli olmayabilir).
  * [`lastindex(str)`](@ref) `str`'ye indekslemek için kullanılabilecek en yüksek (bayt) indeks değerini verir.
  * [`length(str)`](@ref) `str` içindeki karakter sayısı.
  * [`length(str, i, j)`](@ref) `str` içindeki `i` ile `j` arasındaki geçerli karakter indekslerinin sayısı.
  * [`ncodeunits(str)`](@ref) sayısı [code units](https://en.wikipedia.org/wiki/Character_encoding#Terminology) bir dizede.
  * [`codeunit(str, i)`](@ref) dizisi `str` içindeki `i` indeksindeki kod birim değerini verir.
  * [`thisind(str, i)`](@ref) verilen bir dizgede rastgele bir indeks verildiğinde, indeksin işaret ettiği karakterin ilk indeksini bul.
  * [`nextind(str, i, n=1)`](@ref) `i` indeksinden sonra `n`'inci karakterin başlangıcını bul.
  * [`prevind(str, i, n=1)`](@ref) `n`'nci `i`'den önceki karakterin başlangıcını bul.

## [Non-Standard String Literals](@id non-standard-string-literals)

Bir dize oluşturmak veya dize anlamsalını kullanmak istediğiniz durumlar vardır, ancak standart dize yapısının davranışı tam olarak gerekli olan değildir. Bu tür durumlar için, Julia standart dışı dize literalleri sağlar. Standart dışı bir dize literali, normal çift tırnaklı dize literali gibi görünür, ancak hemen bir tanımlayıcı ile önceden gelir ve normal bir dize literali ile farklı davranabilir.

[Regular expressions](@ref man-regex-literals), [byte array literals](@ref man-byte-array-literals), ve [version number literals](@ref man-version-number-literals), aşağıda açıklandığı gibi, standart dışı dize literallerinin bazı örnekleridir. Kullanıcılar ve paketler ayrıca yeni standart dışı dize literalleri tanımlayabilir. Daha fazla belge [Metaprogramming](@ref meta-non-standard-string-literals) bölümünde verilmiştir.

## [Regular Expressions](@id man-regex-literals)

Bazen tam bir dize aramıyorsunuz, ancak belirli bir *deseni* arıyorsunuz. Örneğin, büyük bir metin dosyasından tek bir tarihi çıkarmaya çalıştığınızı varsayalım. O tarihin ne olduğunu bilmiyorsunuz (bu yüzden onu arıyorsunuz), ancak `YYYY-AA-GG` gibi görüneceğini biliyorsunuz. Düzenli ifadeler, bu desenleri belirtmenize ve bunları aramanıza olanak tanır.

Julia, Perl uyumlu düzenli ifadelerin (regex) 2. sürümünü kullanır; bu, [PCRE](https://www.pcre.org/) kütüphanesi tarafından sağlanmaktadır (daha fazla bilgi için [PCRE2 syntax description](https://www.pcre.org/current/doc/html/pcre2syntax.html)'ye bakın). Düzenli ifadeler, iki şekilde dizelerle ilişkilidir: belirgin bağlantı, düzenli ifadelerin dizelerde düzenli desenleri bulmak için kullanılmasıdır; diğer bağlantı ise düzenli ifadelerin kendilerinin, dizeler olarak girilmesidir; bu dizeler, dizelerde desenleri verimli bir şekilde aramak için kullanılabilecek bir durum makinesine ayrıştırılır. Julia'da, düzenli ifadeler, `r` ile başlayan çeşitli tanımlayıcılarla ön eklenmiş standart dışı dize literalleri kullanılarak girilir. Herhangi bir seçenek etkinleştirilmeden kullanılan en temel düzenli ifade literali sadece `r"..."` kullanır:

```jldoctest
julia> re = r"^\s*(?:#|$)"
r"^\s*(?:#|$)"

julia> typeof(re)
Regex
```

Bir regex'in bir dizeyle eşleşip eşleşmediğini kontrol etmek için [`occursin`](@ref) kullanın:

```jldoctest
julia> occursin(r"^\s*(?:#|$)", "not a comment")
false

julia> occursin(r"^\s*(?:#|$)", "# a comment")
true
```

Burada görüldüğü gibi, [`occursin`](@ref) yalnızca verilen regex'in dizede bir eşleşme olup olmadığını belirten true veya false döndürür. Ancak genellikle, bir dize eşleştiğinde, sadece eşleşip eşleşmediğini değil, aynı zamanda *nasıl* eşleştiğini de bilmek istenir. Eşleşme hakkında bu bilgiyi yakalamak için [`match`](@ref) fonksiyonunu kullanın:

```jldoctest
julia> match(r"^\s*(?:#|$)", "not a comment")

julia> match(r"^\s*(?:#|$)", "# a comment")
RegexMatch("#")
```

Eğer düzenli ifade verilen dizeyle eşleşmiyorsa, [`match`](@ref) [`nothing`](@ref) döner - etkileşimli istemde hiçbir şey yazdırmayan özel bir değer. Yazdırmamanın dışında, tamamen normal bir değerdir ve programatik olarak test edebilirsiniz:

```julia
m = match(r"^\s*(?:#|$)", line)
if m === nothing
    println("not a comment")
else
    println("blank or comment")
end
```

Eğer bir düzenli ifade eşleşiyorsa, [`match`](@ref) tarafından döndürülen değer bir [`RegexMatch`](@ref) nesnesidir. Bu nesneler, ifadenin nasıl eşleştiğini kaydeder, eşleşen alt dizeyi ve varsa yakalanan alt dizeleri içerir. Bu örnek yalnızca eşleşen alt dizenin kısmını yakalar, ancak belki de yorum karakterinden sonraki herhangi bir boş olmayan metni yakalamak istiyoruz. Bunu şu şekilde yapabiliriz:

```jldoctest
julia> m = match(r"^\s*(?:#\s*(.*?)\s*$)", "# a comment ")
RegexMatch("# a comment ", 1="a comment")
```

[`match`](@ref) çağrıldığında, aramaya başlamak için bir indeks belirtme seçeneğiniz vardır. Örneğin:

```jldoctest
julia> m = match(r"[0-9]","aaaa1aaaa2aaaa3",1)
RegexMatch("1")

julia> m = match(r"[0-9]","aaaa1aaaa2aaaa3",6)
RegexMatch("2")

julia> m = match(r"[0-9]","aaaa1aaaa2aaaa3",11)
RegexMatch("3")
```

`RegexMatch` nesnesesinden aşağıdaki bilgileri çıkarabilirsiniz:

  * eşleşen tüm alt dize: `m.match`
  * yakalanan alt dizeleri bir dizi dize olarak: `m.captures`
  * eşleşmenin başladığı ofset: `m.offset`
  * yakalanan alt dizelerin ofsetleri bir vektör olarak: `m.offsets`

Bir eşleşme olmadığında, bir alt dize yerine `m.captures` o pozisyonda `nothing` içerir ve `m.offsets` sıfır ofsetine sahiptir (Julia'daki indekslerin 1 tabanlı olduğunu hatırlayın, bu nedenle bir dizeye sıfır ofseti geçersizdir). İşte biraz yapay iki örnek:

```jldoctest acdmatch
julia> m = match(r"(a|b)(c)?(d)", "acd")
RegexMatch("acd", 1="a", 2="c", 3="d")

julia> m.match
"acd"

julia> m.captures
3-element Vector{Union{Nothing, SubString{String}}}:
 "a"
 "c"
 "d"

julia> m.offset
1

julia> m.offsets
3-element Vector{Int64}:
 1
 2
 3

julia> m = match(r"(a|b)(c)?(d)", "ad")
RegexMatch("ad", 1="a", 2=nothing, 3="d")

julia> m.match
"ad"

julia> m.captures
3-element Vector{Union{Nothing, SubString{String}}}:
 "a"
 nothing
 "d"

julia> m.offset
1

julia> m.offsets
3-element Vector{Int64}:
 1
 0
 2
```

Bir dizi olarak dönen yakalamaların olması, bunları yerel değişkenlere bağlamak için yapısal sözdizimini kullanmayı kolaylaştırır. Kolaylık olması açısından, `RegexMatch` nesnesi, `captures` alanına geçiş yapan yineleyici yöntemlerini uygular, böylece eşleşme nesnesini doğrudan yapısal hale getirebilirsiniz:

```jldoctest acdmatch
julia> first, second, third = m; first
"a"
```

Kapsamlar, `RegexMatch` nesnesini yakalama grubunun numarası veya adıyla dizinleyerek de erişilebilir:

```jldoctest
julia> m=match(r"(?<hour>\d+):(?<minute>\d+)","12:45")
RegexMatch("12:45", hour="12", minute="45")

julia> m[:minute]
"45"

julia> m[2]
"45"
```

Yakalamalar, [`replace`](@ref) kullanırken bir yer değiştirme dizesinde referans alınabilir; `\n` kullanarak n'inci yakalama grubuna atıfta bulunabilir ve yer değiştirme dizesini `s` ile öne alabilirsiniz. Yakalama grubu 0, tüm eşleşme nesnesine atıfta bulunur. İsimli yakalama grupları, yer değiştirmede `\g<grupadi>` ile referans alınabilir. Örneğin:

```jldoctest
julia> replace("first second", r"(\w+) (?<agroup>\w+)" => s"\g<agroup> \1")
"second first"
```

Numaralı yakalama grupları, ayrıştırma için `\g<n>` olarak da referans verilebilir, örneğin:

```jldoctest
julia> replace("a", r"." => s"\g<0>1")
"a1"
```

Düzenli ifadelerin davranışını, kapanış çift tırnak işaretinden sonra `i`, `m`, `s` ve `x` bayraklarının bir kombinasyonu ile değiştirebilirsiniz. Bu bayraklar, Perl'deki anlamlarıyla aynı anlama sahiptir; bu, [perlre manpage](https://perldoc.perl.org/perlre#Modifiers) adresinden alınan bu alıntıda açıklandığı gibidir:

```
i   Do case-insensitive pattern matching.

    If locale matching rules are in effect, the case map is taken
    from the current locale for code points less than 255, and
    from Unicode rules for larger code points. However, matches
    that would cross the Unicode rules/non-Unicode rules boundary
    (ords 255/256) will not succeed.

m   Treat string as multiple lines.  That is, change "^" and "$"
    from matching the start or end of the string to matching the
    start or end of any line anywhere within the string.

s   Treat string as single line.  That is, change "." to match any
    character whatsoever, even a newline, which normally it would
    not match.

    Used together, as r""ms, they let the "." match any character
    whatsoever, while still allowing "^" and "$" to match,
    respectively, just after and just before newlines within the
    string.

x   Tells the regular expression parser to ignore most whitespace
    that is neither backslashed nor within a character class. You
    can use this to break up your regular expression into
    (slightly) more readable parts. The '#' character is also
    treated as a metacharacter introducing a comment, just as in
    ordinary code.
```

Örneğin, aşağıdaki regex'in tüm üç bayrağı açık:

```jldoctest
julia> r"a+.*b+.*d$"ism
r"a+.*b+.*d$"ims

julia> match(r"a+.*b+.*d$"ism, "Goodbye,\nOh, angry,\nBad world\n")
RegexMatch("angry,\nBad world")
```

`r"..."` literali, interpolasyon ve kaçış olmadan (yalnızca tırnak işareti `"` hala kaçırılmak zorundadır) oluşturulur. İşte standart dize literallerinden farkı gösteren bir örnek:

```julia-repl
julia> x = 10
10

julia> r"$x"
r"$x"

julia> "$x"
"10"

julia> r"\x"
r"\x"

julia> "\x"
ERROR: syntax: invalid escape sequence
```

Üçlü tırnaklı regex dizeleri, `r"""..."""` biçiminde, desteklenmektedir (ve alıntı işaretleri veya yeni satırlar içeren düzenli ifadeler için kullanışlı olabilir).

`Regex()` yapıcısı, geçerli bir regex dizesini programlı olarak oluşturmak için kullanılabilir. Bu, regex dizesini oluştururken dize değişkenlerinin ve diğer dize işlemlerinin içeriğini kullanmayı mümkün kılar. Yukarıdaki regex kodlarının herhangi biri `Regex()`'in tek dize argümanı içinde kullanılabilir. İşte bazı örnekler:

```jldoctest
julia> using Dates

julia> d = Date(1962,7,10)
1962-07-10

julia> regex_d = Regex("Day " * string(day(d)))
r"Day 10"

julia> match(regex_d, "It happened on Day 10")
RegexMatch("Day 10")

julia> name = "Jon"
"Jon"

julia> regex_name = Regex("[\"( ]\\Q$name\\E[\") ]")  # interpolate value of name
r"[\"( ]\QJon\E[\") ]"

julia> match(regex_name, " Jon ")
RegexMatch(" Jon ")

julia> match(regex_name, "[Jon]") === nothing
true
```

`\Q...\E` kaçış dizisinin kullanımına dikkat edin. `\Q` ve `\E` arasındaki tüm karakterler, literal karakterler olarak yorumlanır. Bu, aksi takdirde regex metakarakterleri olabilecek karakterleri eşleştirmek için kullanışlıdır. Ancak, bu özelliği dize interpolasyonu ile birlikte kullanırken dikkatli olunması gerekir, çünkü interpolasyon yapılan dize kendisi `\E` dizisini içerebilir ve bu da literal eşleşmeyi beklenmedik bir şekilde sonlandırabilir. Kullanıcı girdileri, bir regex'e dahil edilmeden önce temizlenmelidir.

## [Byte Array Literals](@id man-byte-array-literals)

Başka yararlı bir standart dışı dize literalı, byte-dizisi dize literalıdır: `b"..."`. Bu form, yalnızca okunabilir literal byte dizilerini ifade etmek için dize notasyonunu kullanmanıza olanak tanır - yani [`UInt8`](@ref) değerlerinin dizileri. Bu nesnelerin türü `CodeUnits{UInt8, String}`'dir. Byte dizi literal kuralları şunlardır:

  * ASCII karakterleri ve ASCII kaçışları tek bir bayt üretir.
  * `\x` ve sekizli kaçış dizileri, kaçış değerine karşılık gelen *baytı* üretir.
  * Unicode kaçış dizileri, o kod noktasını UTF-8'de kodlayan bir bayt dizisi üretir.

Bu kurallar arasında bazı örtüşmeler vardır çünkü `\x` ve 0x80'den (128) daha küçük sekizli kaçışların davranışı ilk iki kural tarafından kapsanmaktadır, ancak burada bu kurallar hemfikir. Birlikte, bu kuralların hepsi, ASCII karakterlerini, rastgele bayt değerlerini ve UTF-8 dizilerini kullanarak bayt dizileri üretmeyi kolaylaştırır. İşte her üçünü de kullanan bir örnek:

```jldoctest
julia> b"DATA\xff\u2200"
8-element Base.CodeUnits{UInt8, String}:
 0x44
 0x41
 0x54
 0x41
 0xff
 0xe2
 0x88
 0x80
```

ASCII dizisi "DATA" 68, 65, 84, 65 baytlarına karşılık gelir. `\xff` tek bir bayt olan 255'i üretir. Unicode kaçışı `\u2200`, UTF-8'de üç bayt olan 226, 136, 128 olarak kodlanır. Sonuçta elde edilen bayt dizisinin geçerli bir UTF-8 dizesine karşılık gelmediğine dikkat edin:

```jldoctest
julia> isvalid("DATA\xff\u2200")
false
```

`CodeUnits{UInt8, String}` türü, `UInt8`'in yalnızca okunabilir bir dizisi gibi davranır ve standart bir vektöre ihtiyacınız varsa, bunu `Vector{UInt8}` kullanarak dönüştürebilirsiniz:

```jldoctest
julia> x = b"123"
3-element Base.CodeUnits{UInt8, String}:
 0x31
 0x32
 0x33

julia> x[1]
0x31

julia> x[1] = 0x32
ERROR: CanonicalIndexError: setindex! not defined for Base.CodeUnits{UInt8, String}
[...]

julia> Vector{UInt8}(x)
3-element Vector{UInt8}:
 0x31
 0x32
 0x33
```

Ayrıca `\xff` ve `\uff` arasındaki önemli farkı gözlemleyin: ilk kaçış dizisi *byte 255*'i kodlarken, ikincisi *kod noktası 255*'i temsil eder; bu, UTF-8'de iki byte olarak kodlanır:

```jldoctest
julia> b"\xff"
1-element Base.CodeUnits{UInt8, String}:
 0xff

julia> b"\uff"
2-element Base.CodeUnits{UInt8, String}:
 0xc3
 0xbf
```

Karakter literalleri aynı davranışı kullanır.

`<\u80`'den daha düşük kod noktaları için, her kod noktasının UTF-8 kodlamasının, karşılık gelen `\x` kaçışından üretilen tek bayt olduğu durumlar vardır, bu nedenle ayrım güvenle göz ardı edilebilir. Ancak `\x80` ile `\xff` arasındaki kaçışlar ile `\u80` ile `\uff` arasındaki kaçışlar arasında büyük bir fark vardır: ilk kaçışlar tümüyle tek baytları kodlarken, - çok özel devam baytları ile takip edilmediği sürece - geçerli UTF-8 verileri oluşturmazken, sonuncu kaçışlar tümüyle iki baytlı kodlamalarla Unicode kod noktalarını temsil eder.

Eğer bu her şey son derece kafa karıştırıcıysa, ["The Absolute Minimum Every Software Developer Absolutely, Positively Must Know About Unicode and Character Sets"](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/) okuyarak başlayabilirsiniz. Bu, Unicode ve UTF-8'e mükemmel bir giriş niteliğindedir ve konuyla ilgili bazı kafa karışıklıklarını gidermeye yardımcı olabilir.

## [Version Number Literals](@id man-version-number-literals)

Sürüm numaraları, [`v"..."`](@ref @v_str) biçimindeki standart dışı dize literalleri ile kolayca ifade edilebilir. Sürüm numarası literalleri, [semantic versioning](https://semver.org/) spesifikasyonlarını takip eden [`VersionNumber`](@ref) nesneleri oluşturur ve bu nedenle ana, alt ve yaman sayısal değerlerden oluşur, ardından ön sürüm ve yapı alfasayısal notasyonlar gelir. Örneğin, `v"0.2.1-rc1+win64"` ana sürüm `0`, alt sürüm `2`, yaman sürüm `1`, ön sürüm `rc1` ve yapı `win64` olarak ayrılır. Bir sürüm literali girerken, ana sürüm numarası dışındaki her şey isteğe bağlıdır, bu nedenle örneğin `v"0.2"` ifadesi `v"0.2.0"` (boş ön sürüm/yapı notasyonları ile) ile eşdeğerdir, `v"2"` ifadesi `v"2.0.0"` ile eşdeğerdir ve bu şekilde devam eder.

`VersionNumber` nesneleri, iki (veya daha fazla) versiyonu kolayca ve doğru bir şekilde karşılaştırmak için genellikle faydalıdır. Örneğin, sabit [`VERSION`](@ref), Julia sürüm numarasını bir `VersionNumber` nesnesi olarak tutar ve bu nedenle bazı sürüm-spesifik davranışları basit ifadeler kullanarak tanımlamak mümkündür:

```julia
if v"0.2" <= VERSION < v"0.3-"
    # do something specific to 0.2 release series
end
```

Not edin ki yukarıdaki örnekte standart dışı sürüm numarası `v"0.3-"` kullanılmıştır, sonundaki `-` ile: bu notasyon, standartın bir Julia uzantısıdır ve `0.3` sürümünden daha düşük bir sürümü belirtmek için kullanılır, tüm ön sürümleri de dahil. Bu nedenle yukarıdaki örnekte kod yalnızca kararlı `0.2` sürümleri ile çalışacak ve `v"0.3.0-rc1"` gibi sürümleri hariç tutacaktır. Ayrıca kararsız (yani ön sürüm) `0.2` sürümlerine de izin vermek için, alt sınır kontrolü şu şekilde değiştirilmelidir: `v"0.2-" <= VERSION`.

Başka bir standart dışı sürüm spesifikasyonu uzantısı, bir üst sınır ifade etmek için bir `+` eklemeye izin verir; örneğin, `VERSION > v"0.2-rc1+"` ifadesi, `0.2-rc1`'den ve onun herhangi bir derlemesinden daha yüksek olan herhangi bir sürümü ifade etmek için kullanılabilir: `v"0.2-rc1+win64"` sürümü için `false` döner ve `v"0.2-rc2"` için `true` döner.

Özellikle, üst sınırlar için her zaman sonundaki `-` işaretinin kullanılmasının iyi bir uygulama olduğu, ancak bunların herhangi bir şeyin gerçek sürüm numarası olarak kullanılmaması gerektiği, çünkü bunların anlamsal sürümleme şemasında geçersiz olduğu iyi bir uygulamadır.

[`VERSION`](@ref) sabitinin yanı sıra, `VersionNumber` nesneleri `Pkg` modülünde, paket sürümlerini ve bunların bağımlılıklarını belirtmek için yaygın olarak kullanılmaktadır.

## [Raw String Literals](@id man-raw-string-literals)

Hamur string'leri, interpolasyon veya unescape etme olmadan, `raw"..."` biçiminde standart dışı string literalleri ile ifade edilebilir. Hamur string literalleri, içeriklerini tam olarak girildiği gibi, interpolasyon veya unescape etme olmadan içeren sıradan `String` nesneleri oluşturur. Bu, `$` veya `\` gibi özel karakterler kullanan diğer dillerdeki kod veya işaretleme içeren string'ler için faydalıdır.

İstisna, alıntı işaretlerinin hala kaçış karakteri ile gösterilmesi gerektiğidir; örneğin, `raw"\""` ifadesi `"\""` ile eşdeğerdir. Tüm dizeleri ifade edebilmek için, ters eğik çizgilerin de kaçış karakteri ile gösterilmesi gerekir, ancak yalnızca bir alıntı karakterinin hemen önünde göründüğünde:

```jldoctest
julia> println(raw"\\ \\\"")
\\ \"
```

İlk iki ters eğik çizginin çıktıda olduğu gibi göründüğüne dikkat edin, çünkü bunlar bir alıntı karakterinden önce gelmiyor. Ancak, sonraki ters eğik çizgi, onu takip eden ters eğik çizgiyi kaçar ve son ters eğik çizgi bir alıntıyı kaçar, çünkü bu ters eğik çizgiler bir alıntıdan önce gelir.

## [Annotated Strings](@id man-annotated-strings)

!!! note
    AnnotatedStrings API'si deneysel olarak kabul edilmektedir ve Julia sürümleri arasında değişiklik göstermesi muhtemeldir.


Bazen bir dize ile ilgili bölgeleri tutmak için meta verileri saklamak faydalı olabilir. Bir [`AnnotatedString`](@ref Base.AnnotatedString), başka bir dizeyi sarar ve bunun bölgelerinin etiketli değerlerle (`:label => value`) anotasyon yapılmasına olanak tanır. Tüm genel dize işlemleri, temel dizeye uygulanır. Ancak, mümkün olduğunda stil bilgileri korunur. Bu, bir `4d61726b646f776e2e436f64652822222c2022416e6e6f7461746564537472696e672229_4072656620426173652e416e6e6f7461746564537472696e67` üzerinde alt dizeler alabileceğiniz, bunları doldurabileceğiniz, diğer dizelerle birleştirebileceğiniz anlamına gelir ve meta veri anotasyonları "yolda gelir".

Bu dize türü, stil bilgilerini tutmak için `:face` etiketli notasyonlar kullanan [StyledStrings stdlib](@ref stdlib-styledstrings) için temeldir.

[`AnnotatedString`](@ref Base.AnnotatedString) ile birleştirirken, dize açıklamalarını korumak istiyorsanız [`annotatedstring`](@ref Base.annotatedstring) kullanmaya dikkat edin, [`string`](@ref) yerine.

```jldoctest
julia> str = Base.AnnotatedString("hello there",
               [(1:5, :word, :greeting), (7:11, :label, 1)])
"hello there"

julia> length(str)
11

julia> lpad(str, 14)
"   hello there"

julia> typeof(lpad(str, 7))
Base.AnnotatedString{String}

julia> str2 = Base.AnnotatedString(" julia", [(2:6, :face, :magenta)])
" julia"

julia> Base.annotatedstring(str, str2)
"hello there julia"

julia> str * str2 == Base.annotatedstring(str, str2) # *-concatenation still works
true
```

[`AnnotatedString`](@ref Base.AnnotatedString) anotasyonları [`annotations`](@ref Base.annotations) ve [`annotate!`](@ref Base.annotate!) fonksiyonları aracılığıyla erişilebilir ve değiştirilebilir.
