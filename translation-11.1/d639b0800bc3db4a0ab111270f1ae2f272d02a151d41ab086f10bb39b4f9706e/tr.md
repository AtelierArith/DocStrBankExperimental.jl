# Control Flow

Julia, çeşitli kontrol akışı yapıları sunar:

  * [Compound Expressions](@ref man-compound-expressions): `başla` ve `;`.
  * [Conditional Evaluation](@ref man-conditional-evaluation): `eğer`-`eğer değilse`-`değilse` ve `?:` (ternary operatörü).
  * [Short-Circuit Evaluation](@ref): mantıksal operatörler `&&` (“ve”) ve `||` (“veya”), ayrıca zincirleme karşılaştırmalar.
  * [Repeated Evaluation: Loops](@ref man-loops): `while` ve `for`.
  * [Exception Handling](@ref): `denemek`-`yakalamak`, [`error`](@ref) ve [`throw`](@ref).
  * [Tasks (aka Coroutines)](@ref man-tasks): [`yieldto`](@ref).

İlk beş kontrol akışı mekanizması, yüksek seviyeli programlama dilleri için standarttır. [`Task`](@ref) standart değildir: geçici olarak askıya alınmış hesaplamalar arasında geçiş yapmayı mümkün kılarak yerel olmayan kontrol akışı sağlar. Bu güçlü bir yapıdır: hem istisna işleme hem de işbirlikçi çoklu görev, Julia'da görevler kullanılarak uygulanır. Günlük programlama, görevlerin doğrudan kullanımını gerektirmez, ancak belirli problemler görevler kullanılarak çok daha kolay bir şekilde çözülebilir.

## [Compound Expressions](@id man-compound-expressions)

Bazen, birkaç alt ifadenin sırasıyla değerlendirildiği ve son alt ifadenin değerini döndüren tek bir ifadeye sahip olmak kullanışlıdır. Bunu başarmak için iki Julia yapısı vardır: `begin` blokları ve `;` zincirleri. Her iki bileşik ifade yapısının değeri son alt ifadenin değeridir. İşte bir `begin` bloğuna bir örnek:

```jldoctest
julia> z = begin
           x = 1
           y = 2
           x + y
       end
3
```

Bu ifadeler oldukça küçük ve basit olduğundan, kolayca tek bir satıra yerleştirilebilirler; işte bu noktada `;` zincirleme sözdizimi işe yarar:

```jldoctest
julia> z = (x = 1; y = 2; x + y)
3
```

Bu sözdizimi, [Functions](@ref man-functions) ile tanıtılan kısa tek satırlık fonksiyon tanım biçimi ile özellikle kullanışlıdır. Tipik olmasına rağmen, `begin` bloklarının çok satırlı olması veya `;` zincirlerinin tek satırlı olması gerekmez:

```jldoctest
julia> begin x = 1; y = 2; x + y end
3

julia> (x = 1;
        y = 2;
        x + y)
3
```

## [Conditional Evaluation](@id man-conditional-evaluation)

Koşullu değerlendirme, bir boolean ifadesinin değerine bağlı olarak kodun belirli bölümlerinin değerlendirilmesine veya değerlendirilmemesine olanak tanır. İşte `if`-`elseif`-`else` koşullu sözdiziminin anatomisi:

```julia
if x < y
    println("x is less than y")
elseif x > y
    println("x is greater than y")
else
    println("x is equal to y")
end
```

Eğer koşul ifadesi `x < y` `doğru` ise, o zaman ilgili blok değerlendirilir; aksi takdirde koşul ifadesi `x > y` değerlendirilir ve eğer bu `doğru` ise, ilgili blok değerlendirilir; eğer her iki ifade de doğru değilse, `else` bloğu değerlendirilir. İşte burada uygulamada:

```jldoctest
julia> function test(x, y)
           if x < y
               println("x is less than y")
           elseif x > y
               println("x is greater than y")
           else
               println("x is equal to y")
           end
       end
test (generic function with 1 method)

julia> test(1, 2)
x is less than y

julia> test(2, 1)
x is greater than y

julia> test(1, 1)
x is equal to y
```

`elseif` ve `else` blokları isteğe bağlıdır ve istenildiği kadar `elseif` bloğu kullanılabilir. `if`-`elseif`-`else` yapısındaki koşul ifadeleri, ilk `true` değerini döndüren ifade bulunana kadar değerlendirilir; bu noktadan sonra ilişkili blok değerlendirilir ve daha fazla koşul ifadesi veya blok değerlendirilmez.

`if` blokları "sızdıran" yani yerel bir kapsam tanımlamaz. Bu, `if` koşulları içinde tanımlanan yeni değişkenlerin `if` bloğundan sonra da kullanılabileceği anlamına gelir, hatta daha önce tanımlanmamış olsalar bile. Bu nedenle, yukarıdaki `test` fonksiyonunu şu şekilde tanımlayabilirdik:

```jldoctest
julia> function test(x,y)
           if x < y
               relation = "less than"
           elseif x == y
               relation = "equal to"
           else
               relation = "greater than"
           end
           println("x is ", relation, " y.")
       end
test (generic function with 1 method)

julia> test(2, 1)
x is greater than y.
```

Değişken `relation`, `if` bloğu içinde tanımlanmıştır, ancak dışarıda kullanılmaktadır. Ancak, bu davranışa bağlı olarak, tüm olası kod yollarının değişken için bir değer tanımladığından emin olun. Yukarıdaki işlevdeki aşağıdaki değişiklik, bir çalışma zamanı hatasına yol açar.

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> function test(x,y)
           if x < y
               relation = "less than"
           elseif x == y
               relation = "equal to"
           end
           println("x is ", relation, " y.")
       end
test (generic function with 1 method)

julia> test(1,2)
x is less than y.

julia> test(2,1)
ERROR: UndefVarError: `relation` not defined in local scope
Stacktrace:
 [1] test(::Int64, ::Int64) at ./none:7
```

`if` blokları aynı zamanda bir değer döndürür, bu da birçok diğer dilden gelen kullanıcılar için sezgisel olmayabilir. Bu değer, seçilen dalda yürütülen son ifadenin döndürdüğü değerdir, bu nedenle

```jldoctest
julia> x = 3
3

julia> if x > 0
           "positive!"
       else
           "negative..."
       end
"positive!"
```

Kısa koşullu ifadelerin (tek satırlık) genellikle Julia'da Kısa Devre Değerlendirmesi kullanılarak ifade edildiğini unutmayın; bu, bir sonraki bölümde açıklanmıştır.

C, MATLAB, Perl, Python ve Ruby'den farklı olarak - ancak Java ve birkaç diğer daha katı, tipli diller gibi - bir koşullu ifadenin değeri `true` veya `false` dışında bir şey olduğunda bir hata oluşur:

```jldoctest
julia> if 1
           println("true")
       end
ERROR: TypeError: non-boolean (Int64) used in boolean context
```

Bu hata, koşulun yanlış türde olduğunu gösterir: [`Int64`](@ref) yerine gereken [`Bool`](@ref).

Sözde "üçlü operatör", `?:`, `if`-`elseif`-`else` sözdizimi ile yakından ilişkilidir, ancak daha uzun kod bloklarının koşullu yürütülmesi yerine tek ifade değerleri arasında koşullu bir seçim gerektiğinde kullanılır. Üç operand alan tek operatör olduğu için bu ismi alır:

```julia
a ? b : c
```

`a` ifadesi, `?` öncesinde bir koşul ifadesidir ve üçlü işlem, koşul `a` `true` ise `:` öncesindeki `b` ifadesini, `false` ise `:` sonrasındaki `c` ifadesini değerlendirir. `?` ve `:` etrafındaki boşlukların zorunlu olduğunu unutmayın: `a?b:c` gibi bir ifade geçerli bir üçlü ifade değildir (ancak `?` ve `:` sonrasında bir satır sonu kabul edilebilir).

Bu davranışı anlamanın en kolay yolu bir örneğe bakmaktır. Önceki örnekte, `println` çağrısı üç dal tarafından paylaşılmaktadır: tek gerçek seçim, hangi sabit dizeyi yazdırmaktır. Bu, üçlü operatör kullanılarak daha öz bir şekilde yazılabilir. Açıklık adına, önce iki yönlü bir versiyonunu deneyelim:

```jldoctest
julia> x = 1; y = 2;

julia> println(x < y ? "less than" : "not less than")
less than

julia> x = 1; y = 0;

julia> println(x < y ? "less than" : "not less than")
not less than
```

Eğer `x < y` ifadesi doğruysa, tüm üçlü operatör ifadesi `"less than"` stringine değer verir, aksi takdirde `"not less than"` stringine değer verir. Orijinal üçlü örnek, üçlü operatörün birden fazla kullanımını bir araya getirmeyi gerektirir:

```jldoctest
julia> test(x, y) = println(x < y ? "x is less than y"    :
                            x > y ? "x is greater than y" : "x is equal to y")
test (generic function with 1 method)

julia> test(1, 2)
x is less than y

julia> test(2, 1)
x is greater than y

julia> test(1, 1)
x is equal to y
```

Zincirleme işlemleri kolaylaştırmak için, operatör sağdan sola doğru ilişkilendirilir.

Önemli olan, `if`-`elseif`-`else` gibi, `:` öncesindeki ve sonrasındaki ifadelerin yalnızca koşul ifadesi `true` veya `false` olarak değerlendirildiğinde sırasıyla değerlendirildiğidir:

```jldoctest
julia> v(x) = (println(x); x)
v (generic function with 1 method)

julia> 1 < 2 ? v("yes") : v("no")
yes
"yes"

julia> 1 > 2 ? v("yes") : v("no")
no
"no"
```

## Short-Circuit Evaluation

`&&` ve `||` operatörleri Julia'da mantıksal "ve" ve "veya" işlemlerine karşılık gelir ve genellikle bu amaçla kullanılır. Ancak, ek bir *kısa devre* değerlendirme özelliğine sahiptirler: ikinci argümanlarını mutlaka değerlendirmezler, aşağıda açıklandığı gibi. (Kısa devre davranışı olmadan mantıksal "ve" ve "veya" olarak kullanılabilen bit düzeyinde `&` ve `|` operatörleri de vardır, ancak `&` ve `|`'nin değerlendirme sırası için `&&` ve `||`'dan daha yüksek önceliğe sahip olduğunu unutmayın.)

Kısa devre değerlendirmesi, koşullu değerlendirmeye oldukça benzer. Bu davranış, `&&` ve `||` boolean operatörlerine sahip olan çoğu imperatif programlama dilinde bulunur: bu operatörlerle bağlı bir dizi boolean ifadesinde, tüm zincirin nihai boolean değerini belirlemek için gerekli olan minimum sayıda ifade değerlendirilir. Bazı diller (Python gibi) bunları `and` (`&&`) ve `or` (`||`) olarak adlandırır. Açıkça, bu şu anlama gelir:

  * `a && b` ifadesinde, `b` alt ifadesi yalnızca `a` ifadesi `true` olarak değerlendirildiğinde değerlendirilir.
  * `a || b` ifadesinde, `b` alt ifadesi yalnızca `a` ifadesi `false` olarak değerlendiğinde değerlendirilir.

Mantık, `a && b` ifadesinin `a` yanlışsa `false` olması gerektiğidir, `b`'nin değeri ne olursa olsun, ve benzer şekilde, `a || b` ifadesinin `a` doğruysa `true` olması gerektiğidir, `b`'nin değeri ne olursa olsun. Hem `&&` hem de `||` sağa doğru bağlanır, ancak `&&`'nin önceliği `||`'den daha yüksektir. Bu davranışı denemek kolaydır:

```jldoctest tandf
julia> t(x) = (println(x); true)
t (generic function with 1 method)

julia> f(x) = (println(x); false)
f (generic function with 1 method)

julia> t(1) && t(2)
1
2
true

julia> t(1) && f(2)
1
2
false

julia> f(1) && t(2)
1
false

julia> f(1) && f(2)
1
false

julia> t(1) || t(2)
1
true

julia> t(1) || f(2)
1
true

julia> f(1) || t(2)
1
2
true

julia> f(1) || f(2)
1
2
false
```

`&&` ve `||` operatörlerinin çeşitli kombinasyonlarının birleşim sırası ve önceliği ile aynı şekilde kolayca deney yapabilirsiniz.

Bu davranış, Julia'da çok kısa `if` ifadelerine alternatif oluşturmak için sıklıkla kullanılır. `if <cond> <statement> end` yerine, `<cond> && <statement>` yazılabilir (bu, <cond> *ve sonra* <statement> olarak okunabilir). Benzer şekilde, `if ! <cond> <statement> end` yerine, `<cond> || <statement>` yazılabilir (bu, <cond> *ya da* <statement> olarak okunabilir).

Örneğin, bir özyinelemeli faktöriyel rutini şu şekilde tanımlanabilir:

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> function fact(n::Int)
           n >= 0 || error("n must be non-negative")
           n == 0 && return 1
           n * fact(n-1)
       end
fact (generic function with 1 method)

julia> fact(5)
120

julia> fact(0)
1

julia> fact(-1)
ERROR: n must be non-negative
Stacktrace:
 [1] error at ./error.jl:33 [inlined]
 [2] fact(::Int64) at ./none:2
 [3] top-level scope
```

Boolean işlemleri *kısa devre* değerlendirmesi olmadan, [Mathematical Operations and Elementary Functions](@ref)'da tanıtılan bit düzeyindeki boolean operatörleri ile yapılabilir: `&` ve `|`. Bunlar normal fonksiyonlardır, infiks operatör sözdizimini desteklerler, ancak her zaman argümanlarını değerlendirirler:

```jldoctest tandf
julia> f(1) & t(2)
1
2
false

julia> t(1) | t(2)
1
2
true
```

`if`, `elseif` veya üçlü operatörde kullanılan koşul ifadeleri gibi, `&&` veya `||` operatörlerinin operandları boolean değerler (`true` veya `false`) olmalıdır. Koşullu bir zincirde son giriş dışında herhangi bir yerde boolean olmayan bir değer kullanmak bir hatadır:

```jldoctest
julia> 1 && true
ERROR: TypeError: non-boolean (Int64) used in boolean context
```

Diğer yandan, bir koşul zincirinin sonunda her türlü ifade kullanılabilir. Bu ifade, önceki koşullara bağlı olarak değerlendirilecek ve döndürülecektir:

```jldoctest
julia> true && (x = (1, 2, 3))
(1, 2, 3)

julia> false && (x = (1, 2, 3))
false
```

## [Repeated Evaluation: Loops](@id man-loops)

İfadelerin tekrar değerlendirilmesi için iki yapı vardır: `while` döngüsü ve `for` döngüsü. İşte bir `while` döngüsü örneği:

```jldoctest
julia> i = 1;

julia> while i <= 3
           println(i)
           global i += 1
       end
1
2
3
```

`while` döngüsü koşul ifadesini (`i <= 3` bu durumda) değerlendirir ve bu ifade `true` olduğu sürece `while` döngüsünün gövdesini de değerlendirmeye devam eder. Eğer koşul ifadesi `while` döngüsüne ilk ulaşıldığında `false` ise, gövde asla değerlendirilmez.

`for` döngüsü, yaygın tekrar eden değerlendirme kalıplarını yazmayı kolaylaştırır. Yukarıdaki `while` döngüsü gibi yukarı ve aşağı saymak çok yaygın olduğundan, daha özlü bir şekilde `for` döngüsü ile ifade edilebilir:

```jldoctest
julia> for i = 1:3
           println(i)
       end
1
2
3
```

Burada `1:3`, 1, 2, 3 sayı dizisini temsil eden bir [`range`](@ref) nesnesidir. `for` döngüsü bu değerler üzerinde yineleyerek her birini sırayla `i` değişkenine atar. Genel olarak, `for` yapısı `1:3` veya `1:3:13` gibi herhangi bir "iterable" nesne (veya "kapsayıcı") üzerinde döngü oluşturabilir (her 3. tam sayıyı gösteren bir [`StepRange`](@ref), 1, 4, 7, …, 13) veya diziler gibi daha genel kapsayıcılara, [iterators defined by user code](@ref man-interface-iteration) veya harici paketler. Aralıklar dışındaki kapsayıcılar için, kodun daha net okunmasını sağladığı için genellikle `=` yerine `in` veya `∈` anahtar kelimesi kullanılır.

```jldoctest
julia> for i in [1,4,0]
           println(i)
       end
1
4
0

julia> for s ∈ ["foo","bar","baz"]
           println(s)
       end
foo
bar
baz
```

Farklı türdeki yineleyici konteynerler, kılavuzun ilerleyen bölümlerinde tanıtılacak ve tartışılacaktır (bkz. örneğin, [Multi-dimensional Arrays](@ref man-multi-dim-arrays)).

Bir önceki `while` döngüsü biçimi ile `for` döngüsü biçimi arasındaki oldukça önemli bir ayrım, değişkenin görünür olduğu kapsamdır. Bir `for` döngüsü, kapsayıcı kapsamda aynı isimde bir değişken bulunsa bile, her zaman gövdesinde yeni bir yineleme değişkeni tanıtır. Bu, bir yandan `i`'nin döngüden önce tanımlanmasına gerek olmadığı anlamına gelir. Öte yandan, döngü dışında görünür olmayacak ve aynı isimdeki dış değişken de etkilenmeyecektir. Bunu test etmek için ya yeni bir etkileşimli oturum örneğine ya da farklı bir değişken adına ihtiyacınız olacak:

```jldoctest
julia> for j = 1:3
           println(j)
       end
1
2
3

julia> j
ERROR: UndefVarError: `j` not defined in `Main`
```

```jldoctest
julia> j = 0;

julia> for j = 1:3
           println(j)
       end
1
2
3

julia> j
0
```

`for outer` kullanarak son davranışı değiştirin ve mevcut bir yerel değişkeni yeniden kullanın.

[Scope of Variables](@ref scope-of-variables) değişken kapsamı hakkında ayrıntılı bir açıklama için, [`outer`](@ref) ve Julia'da nasıl çalıştığı hakkında bilgi edinin.

Bazen, bir `while` döngüsünün test koşulu yanlışlanmadan önce tekrarı sonlandırmak veya bir `for` döngüsünde yineleyici nesnenin sonuna ulaşmadan önce yinelemeyi durdurmak pratik olabilir. Bu, `break` anahtar kelimesi ile gerçekleştirilebilir:

```jldoctest
julia> i = 1;

julia> while true
           println(i)
           if i >= 3
               break
           end
           global i += 1
       end
1
2
3

julia> for j = 1:1000
           println(j)
           if j >= 3
               break
           end
       end
1
2
3
```

`break` anahtar kelimesi olmadan, yukarıdaki `while` döngüsü kendi başına asla sona ermeyecek ve `for` döngüsü 1000'e kadar dönecektir. Bu döngüler, `break` kullanılarak erken bir şekilde sonlandırılır.

Başka durumlarda, bir yinelemeyi durdurup hemen bir sonrakine geçebilmek faydalıdır. `continue` anahtar kelimesi bunu başarır:

```jldoctest
julia> for i = 1:10
           if i % 3 != 0
               continue
           end
           println(i)
       end
3
6
9
```

Bu, durumu olumsuzlayarak ve `println` çağrısını `if` bloğunun içine yerleştirerek aynı davranışı daha net bir şekilde üretebileceğimiz için biraz yapay bir örnektir. Gerçekçi kullanımda, `continue`'dan sonra değerlendirilecek daha fazla kod vardır ve genellikle `continue` çağrısının yapıldığı birden fazla nokta vardır.

Birden fazla iç içe `for` döngüsü, dıştaki bir döngüde birleştirilerek, iterabl'larının kartezyen çarpımını oluşturabilir:

```jldoctest
julia> for i = 1:2, j = 3:4
           println((i, j))
       end
(1, 3)
(1, 4)
(2, 3)
(2, 4)
```

Bu sözdizimi ile, yine de dış döngü değişkenlerine atıfta bulunabilen yinelemeler olabilir; örneğin, `for i = 1:n, j = 1:i` geçerlidir. Ancak, böyle bir döngü içinde bir `break` ifadesi, yalnızca iç döngüyü değil, tüm döngü kümesini terk eder. Her iç döngü çalıştığında, her iki değişken (`i` ve `j`) de mevcut yineleme değerlerine ayarlanır. Bu nedenle, `i`'ye yapılan atamalar sonraki yinelemelerde görünür olmayacaktır:

```jldoctest
julia> for i = 1:2, j = 3:4
           println((i, j))
           i = 0
       end
(1, 3)
(1, 4)
(2, 3)
(2, 4)
```

Eğer bu örnek, her bir değişken için `for` anahtar kelimesi kullanılarak yeniden yazılsaydı, çıktı farklı olurdu: ikinci ve dördüncü değerler `0` içerirdi.

Birden fazla konteyner, tek bir `for` döngüsü içinde aynı anda yineleyebilir: [`zip`](@ref)

```jldoctest
julia> for (j, k) in zip([1 2 3], [4 5 6 7])
           println((j,k))
       end
(1, 4)
(2, 5)
(3, 6)
```

[`zip`](@ref) kullanarak, ona geçirilen konteynerler için alt yineleyicileri içeren bir demet oluşturan bir yineleyici oluşturulacaktır. `zip` yineleyicisi, her `for` döngüsünün $i$'nci yinelemesinde her alt yineleyicinin $i$'nci elemanını seçerek, tüm alt yineleyiciler üzerinde sırayla yineleme yapacaktır. Herhangi bir alt yineleyici tükenirse, `for` döngüsü duracaktır.

## Exception Handling

Beklenmedik bir durum meydana geldiğinde, bir fonksiyon çağrısına makul bir değer döndüremeyebilir. Bu tür durumlarda, olağanüstü durumun ya bir tanı hata mesajı yazdırarak programı sonlandırması ya da programcının bu tür olağanüstü durumları ele almak için kod sağlamışsa, o kodun uygun eylemi gerçekleştirmesine izin vermesi en iyisi olabilir.

### Built-in `Exception`s

`Exception`lar, beklenmedik bir durum meydana geldiğinde fırlatılır. Aşağıda listelenen yerleşik `Exception`lar, normal kontrol akışını kesintiye uğratır.

| `Exception`                   |
|:----------------------------- |
| [`ArgumentError`](@ref)       |
| [`BoundsError`](@ref)         |
| [`CompositeException`](@ref)  |
| [`DimensionMismatch`](@ref)   |
| [`DivideError`](@ref)         |
| [`DomainError`](@ref)         |
| [`EOFError`](@ref)            |
| [`ErrorException`](@ref)      |
| [`InexactError`](@ref)        |
| [`InitError`](@ref)           |
| [`InterruptException`](@ref)  |
| `InvalidStateException`       |
| [`KeyError`](@ref)            |
| [`LoadError`](@ref)           |
| [`OutOfMemoryError`](@ref)    |
| [`ReadOnlyMemoryError`](@ref) |
| [`RemoteException`](@ref)     |
| [`MethodError`](@ref)         |
| [`OverflowError`](@ref)       |
| [`Meta.ParseError`](@ref)     |
| [`SystemError`](@ref)         |
| [`TypeError`](@ref)           |
| [`UndefRefError`](@ref)       |
| [`UndefVarError`](@ref)       |
| [`StringIndexError`](@ref)    |

Örneğin, [`sqrt`](@ref) fonksiyonu, negatif bir reel değere uygulandığında [`DomainError`](@ref) hatası fırlatır:

```jldoctest
julia> sqrt(-1)
ERROR: DomainError with -1.0:
sqrt was called with a negative real argument but will only return a complex result if called with a complex argument. Try sqrt(Complex(x)).
Stacktrace:
[...]
```

Kendi özel istisnalarınızı aşağıdaki şekilde tanımlayabilirsiniz:

```jldoctest
julia> struct MyCustomException <: Exception end
```

### The [`throw`](@ref) function

Ayrıcalıklar, [`throw`](@ref) ile açıkça oluşturulabilir. Örneğin, yalnızca negatif olmayan sayılar için tanımlanmış bir fonksiyon, negatif bir argüman varsa `4d61726b646f776e2e436f64652822222c20227468726f772229_40726566` bir [`DomainError`](@ref) olarak yazılabilir:

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> f(x) = x>=0 ? exp(-x) : throw(DomainError(x, "argument must be non-negative"))
f (generic function with 1 method)

julia> f(1)
0.36787944117144233

julia> f(-1)
ERROR: DomainError with -1:
argument must be non-negative
Stacktrace:
 [1] f(::Int64) at ./none:1
```

[`DomainError`](@ref) parantezsiz bir istisna değildir, ancak bir istisna türüdür. Bir `Exception` nesnesi elde etmek için çağrılması gerekir:

```jldoctest
julia> typeof(DomainError(nothing)) <: Exception
true

julia> typeof(DomainError) <: Exception
false
```

Ayrıca, bazı istisna türleri hata raporlaması için kullanılan bir veya daha fazla argüman alır:

```jldoctest
julia> throw(UndefVarError(:x))
ERROR: UndefVarError: `x` not defined
```

Bu mekanizma, [`UndefVarError`](@ref) şeklinde yazıldığı gibi özel istisna türleri ile kolayca uygulanabilir:

```jldoctest
julia> struct MyUndefVarError <: Exception
           var::Symbol
       end

julia> Base.showerror(io::IO, e::MyUndefVarError) = print(io, e.var, " not defined")
```

!!! note
    Hata mesajı yazarken, ilk kelimenin küçük harfle başlaması tercih edilir. Örneğin,

    `size(A) == size(B) || throw(DimensionMismatch("A'nın boyutu B'nin boyutuna eşit değil"))`

    tercih edilir

    `size(A) == size(B) || throw(DimensionMismatch("A'nın boyutu B'nin boyutuna eşit değil"))`.

    Ancak, bazen bir işlevin argümanı büyük harf ise, ilk harfi büyük tutmak mantıklıdır:

    `size(A,1) == size(B,2) || throw(DimensionMismatch("A'nın ilk boyutu..."))`.


### Errors

[`error`](@ref) fonksiyonu, normal kontrol akışını kesen bir [`ErrorException`](@ref) üretmek için kullanılır.

Negatif bir sayının karekökü alındığında yürütmeyi hemen durdurmak istiyorsak, negatif bir argüman alındığında hata veren [`sqrt`](@ref) fonksiyonunun bulanık bir versiyonunu tanımlayabiliriz:

```jldoctest fussy_sqrt; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> fussy_sqrt(x) = x >= 0 ? sqrt(x) : error("negative x not allowed")
fussy_sqrt (generic function with 1 method)

julia> fussy_sqrt(2)
1.4142135623730951

julia> fussy_sqrt(-1)
ERROR: negative x not allowed
Stacktrace:
 [1] error at ./error.jl:33 [inlined]
 [2] fussy_sqrt(::Int64) at ./none:1
 [3] top-level scope
```

Eğer `fussy_sqrt` başka bir fonksiyondan negatif bir değerle çağrılırsa, çağıran fonksiyonun yürütülmesine devam etmeye çalışmak yerine hemen döner ve hata mesajını etkileşimli oturumda görüntüler:

```jldoctest fussy_sqrt; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> function verbose_fussy_sqrt(x)
           println("before fussy_sqrt")
           r = fussy_sqrt(x)
           println("after fussy_sqrt")
           return r
       end
verbose_fussy_sqrt (generic function with 1 method)

julia> verbose_fussy_sqrt(2)
before fussy_sqrt
after fussy_sqrt
1.4142135623730951

julia> verbose_fussy_sqrt(-1)
before fussy_sqrt
ERROR: negative x not allowed
Stacktrace:
 [1] error at ./error.jl:33 [inlined]
 [2] fussy_sqrt at ./none:1 [inlined]
 [3] verbose_fussy_sqrt(::Int64) at ./none:3
 [4] top-level scope
```

### The `try/catch` statement

`try/catch` ifadesi, `Exception`'ların test edilmesine ve uygulamanızı normalde kırabilecek şeylerin zarif bir şekilde ele alınmasına olanak tanır. Örneğin, aşağıdaki kodda karekök fonksiyonu normalde bir istisna fırlatır. Bunu etrafında bir `try/catch` bloğu yerleştirerek burada hafifletebiliriz. Bu istisnayı nasıl ele alacağınızı seçebilirsiniz; bunu kaydetmek, bir yer tutucu değeri döndürmek veya aşağıdaki durumda olduğu gibi sadece bir ifade yazdırmak gibi. Beklenmedik durumları ele alırken düşünmeniz gereken bir şey, `try/catch` bloğu kullanmanın, bu durumları ele almak için koşullu dallanma kullanmaktan çok daha yavaş olduğudur. Aşağıda, `try/catch` bloğu ile istisnaları ele almanın daha fazla örneği bulunmaktadır:

```jldoctest
julia> try
           sqrt("ten")
       catch e
           println("You should have entered a numeric value")
       end
You should have entered a numeric value
```

`try/catch` ifadeleri ayrıca `Exception`'ı bir değişkende saklamaya da olanak tanır. Aşağıdaki yapay örnek, `x` indekslenebilir ise `x`'in ikinci elemanının karekökünü hesaplar, aksi takdirde `x`'in bir reel sayı olduğunu varsayar ve karekökünü döndürür:

```jldoctest
julia> sqrt_second(x) = try
           sqrt(x[2])
       catch y
           if isa(y, DomainError)
               sqrt(complex(x[2], 0))
           elseif isa(y, BoundsError)
               sqrt(x)
           end
       end
sqrt_second (generic function with 1 method)

julia> sqrt_second([1 4])
2.0

julia> sqrt_second([1 -4])
0.0 + 2.0im

julia> sqrt_second(9)
3.0

julia> sqrt_second(-9)
ERROR: DomainError with -9.0:
sqrt was called with a negative real argument but will only return a complex result if called with a complex argument. Try sqrt(Complex(x)).
Stacktrace:
[...]
```

`catch` ifadesinden sonraki sembolün her zaman istisna için bir ad olarak yorumlanacağını unutmayın, bu nedenle tek satırda `try/catch` ifadeleri yazarken dikkatli olunmalıdır. Aşağıdaki kod, bir hata durumunda `x` değerini döndürmek için *çalışmayacaktır*:

```julia
try bad() catch x end
```

Bunun yerine, `catch` ifadesinden sonra bir noktalı virgül kullanın veya bir satır sonu ekleyin:

```julia
try bad() catch; x end

try bad()
catch
    x
end
```

`try/catch` yapısının gücü, derinlemesine iç içe geçmiş bir hesaplamayı hemen çağıran fonksiyonlar yığınında çok daha yüksek bir seviyeye geri sarmak yeteneğinde yatmaktadır. Hata oluşmamış durumlar da vardır, ancak yığını geri sarmak ve bir değeri daha yüksek bir seviyeye iletmek istenebilir. Julia, daha gelişmiş hata yönetimi için [`rethrow`](@ref), [`backtrace`](@ref), [`catch_backtrace`](@ref) ve [`current_exceptions`](@ref) fonksiyonlarını sunmaktadır.

### `else` Clauses

!!! compat "Julia 1.8"
    Bu işlevsellik en az Julia 1.8 gerektirir.


Bazen, birinin yalnızca hata durumunu uygun bir şekilde ele almakla kalmayıp, aynı zamanda `try` bloğu başarılı olduğunda yalnızca bazı kodları çalıştırmak istemesi mümkündür. Bunun için, daha önce herhangi bir hata atılmadığında çalıştırılan bir `catch` bloğundan sonra belirtilen bir `else` ifadesi kullanılabilir. Bu kodun `try` bloğuna dahil edilmesine göre avantajı, daha fazla hatanın `catch` ifadesi tarafından sessizce yakalanmamasıdır.

```julia
local x
try
    x = read("file", String)
catch
    # handle read errors
else
    # do something with x
end
```

!!! note
    `try`, `catch`, `else` ve `finally` kısımları her biri kendi kapsam bloklarını tanıtır, bu nedenle bir değişken yalnızca `try` bloğunda tanımlanmışsa, `else` veya `finally` kısımları tarafından erişilemez:

    ```jldoctest
    julia> try
               foo = 1
           catch
           else
               foo
           end
    ERROR: UndefVarError: `foo` not defined in `Main`
    Suggestion: check for spelling errors or missing imports.
    ```

    [`local` keyword](@ref local-scope) dışındaki `try` bloğunun, değişkenin dış kapsamda her yerden erişilebilir olmasını sağlamak için kullanın.


### `finally` Clauses

Kodun durum değişiklikleri gerçekleştirdiği veya dosyalar gibi kaynaklar kullandığı durumlarda, genellikle kod tamamlandığında yapılması gereken temizleme işleri (örneğin dosyaları kapatma) vardır. İstisnalar bu görevi karmaşık hale getirebilir, çünkü bir kod bloğunun normal sonuna ulaşmadan çıkmasına neden olabilirler. `finally` anahtar kelimesi, belirli bir kod bloğu çıkarken, çıkış şekli ne olursa olsun bazı kodların çalıştırılmasını sağlar.

Örneğin, açılmış bir dosyanın kapatıldığından nasıl emin olabileceğimiz burada:

```julia
f = open("file")
try
    # operate on file f
finally
    close(f)
end
```

`try` bloğundan kontrol çıktığında (örneğin bir `return` nedeniyle veya normal bir şekilde sona erdiğinde), `close(f)` çalıştırılacaktır. Eğer `try` bloğu bir istisna nedeniyle çıkarsa, istisna yayılmaya devam edecektir. Bir `catch` bloğu `try` ve `finally` ile birleştirilebilir. Bu durumda `finally` bloğu, `catch` hatayı işledikten sonra çalışacaktır.

## [Tasks (aka Coroutines)](@id man-tasks)

Görevler, hesaplamaların esnek bir şekilde askıya alınmasına ve yeniden başlatılmasına olanak tanıyan bir kontrol akışı özelliğidir. Tam bir tartışma için burada yalnızca tamamlayıcılık açısından bahsediyoruz; tam bir tartışma için bkz. [Asynchronous Programming](@ref man-asynchronous).
