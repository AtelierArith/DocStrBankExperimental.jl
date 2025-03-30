# [Functions](@id man-functions)

Julia'da bir fonksiyon, bir argüman değerleri demetini bir dönüş değerine eşleyen bir nesnedir. Julia fonksiyonları saf matematiksel fonksiyonlar değildir, çünkü programın küresel durumunu değiştirebilir ve ondan etkilenebilirler. Julia'da fonksiyon tanımlamanın temel sözdizimi şudur:

```jldoctest
julia> function f(x, y)
           x + y
       end
f (generic function with 1 method)
```

Bu fonksiyon `x` ve `y` adlı iki argümanı kabul eder ve son değerlendirilen ifadenin değerini, yani `x + y`'yi döndürür.

Julia'da bir fonksiyon tanımlamak için daha kısa bir sözdizimi vardır. Yukarıda gösterilen geleneksel fonksiyon bildirim sözdizimi, aşağıdaki kompakt "atama biçimi" ile eşdeğerdir:

```jldoctest fofxy
julia> f(x, y) = x + y
f (generic function with 1 method)
```

In the assignment form, the body of the function must be a single expression, although it can be a compound expression (see [Compound Expressions](@ref man-compound-expressions)). Short, simple function definitions are common in Julia. The short function syntax is accordingly quite idiomatic, considerably reducing both typing and visual noise.

Bir fonksiyon, geleneksel parantez sözdizimi kullanılarak çağrılır:

```jldoctest fofxy
julia> f(2, 3)
5
```

Parantezsiz, `f` ifadesi fonksiyon nesnesine atıfta bulunur ve diğer değerler gibi taşınabilir:

```jldoctest fofxy
julia> g = f;

julia> g(2, 3)
5
```

Değişkenlerde olduğu gibi, Unicode fonksiyon adları için de kullanılabilir:

```jldoctest
julia> ∑(x, y) = x + y
∑ (generic function with 1 method)

julia> ∑(2, 3)
5
```

## [Argument Passing Behavior](@id man-argument-passing)

Julia işlev argümanları, "paylaşım yoluyla geçiş" olarak adlandırılan bir geleneği takip eder; bu, değerlerin işlevlere geçildiğinde kopyalanmadığı anlamına gelir. İşlev argümanları, değerleri referans alabilen yeni değişken *bağlantıları* (yeni "isimler") olarak işlev görür; tıpkı [assignments](@ref man-assignment-expressions) `argument_name = argument_value` gibi, böylece referans aldıkları nesneler, geçirilen değerlerle özdeştir. Bir işlev içinde yapılan değişiklikler, değiştirilebilir değerler (örneğin `Array`ler) üzerinde, çağıran tarafından görülebilir. (Bu, Scheme, çoğu Lisp, Python, Ruby ve Perl gibi diğer dinamik dillerde bulunan aynı davranıştır.)

Örneğin, fonksiyonda

```julia
function f(x, y)
    x[1] = 42    # mutates x
    y = 7 + y    # new binding for y, no mutation
    return y
end
```

`x[1] = 42` ifadesi `x` nesnesini *değiştirir* ve bu nedenle bu değişiklik, bu argüman için çağıran tarafından geçirilen dizide *görünecektir*. Öte yandan, `y = 7 + y` ataması, *orijinal* nesneyi değiştirmek yerine `y` adını yeni bir değer olan `7 + y` ile ilişkilendirir ve bu nedenle çağıran tarafından geçirilen ilgili argümanı *değiştirmez*. Bu, `f(x, y)` çağrıldığında görülebilir:

```julia-repl
julia> a = [4, 5, 6]
3-element Vector{Int64}:
 4
 5
 6

julia> b = 3
3

julia> f(a, b) # returns 7 + b == 10
10

julia> a  # a[1] is changed to 42 by f
3-element Vector{Int64}:
 42
  5
  6

julia> b  # not changed
3
```

Julia'da yaygın bir gelenek olarak (sözdizimsel bir gereklilik olmamakla birlikte), böyle bir fonksiyon [typically be named `f!(x, y)`](@ref man-punctuation) yerine `f(x, y)` şeklinde adlandırılır; bu, çağrı noktasında en az bir argümanın (genellikle ilk olan) değiştirildiğini görsel bir hatırlatıcı olarak belirtir.

!!! warning "Shared memory between arguments"
    Bir mutasyona uğrayan fonksiyonun davranışı, bir mutasyona uğramış argümanın başka bir argümanla bellek paylaşması durumunda, yani aliasing durumunda (örneğin, birinin diğerinin görünümü olduğu durumlarda) beklenmedik olabilir. Fonksiyonun dokümantasyon dizesi, aliasing'in beklenen sonucu ürettiğini açıkça belirtmedikçe, bu tür girdilerde doğru davranışı sağlamak çağıran kişinin sorumluluğundadır.


## Argument-type declarations

Fonksiyon argümanlarının türlerini, argüman adının sonuna `::TypeName` ekleyerek belirtebilirsiniz, bu da Julia'daki [Type Declarations](@ref) için alışıldık bir yöntemdir. Örneğin, aşağıdaki fonksiyon [Fibonacci numbers](https://en.wikipedia.org/wiki/Fibonacci_number)'i özyinelemeli olarak hesaplar:

```
fib(n::Integer) = n ≤ 2 ? one(n) : fib(n-1) + fib(n-2)
```

ve `::Integer` spesifikasyonu, `n`'nin [abstract](@ref man-abstract-types) `Integer` türünün bir alt türü olduğunda yalnızca çağrılabilir olacağı anlamına gelir.

Argument türü bildirimleri **genellikle performans üzerinde hiçbir etkiye sahip değildir**: hangi argüman türlerinin (varsa) bildirildiğine bakılmaksızın, Julia çağrıcı tarafından geçirilen gerçek argüman türleri için işlevin özel bir versiyonunu derler. Örneğin, `fib(1)` çağrısı, `Int` argümanları için özel olarak optimize edilmiş `fib`'in derlenmesini tetikler; bu, `fib(7)` veya `fib(15)` çağrıldığında yeniden kullanılır. (Bir argüman türü bildiriminin ek derleyici özel durumlarını tetikleyebileceği nadir istisnalar vardır; bkz: [Be aware of when Julia avoids specializing](@ref).) Julia'da argüman türlerini bildirmenin en yaygın nedenleri ise şunlardır:

  * **Gönderim:** [Methods](@ref)'da açıklandığı gibi, farklı argüman türleri için bir fonksiyonun farklı sürümlerine ("yöntemler") sahip olabilirsiniz; bu durumda hangi argümanların hangi uygulamanın çağrılacağını belirlemek için argüman türleri kullanılır. Örneğin, `fib(x::Number) = ...` şeklinde, herhangi bir `Number` türü için çalışan tamamen farklı bir algoritma uygulayabilirsiniz; bunu [Binet's formula](https://en.wikipedia.org/wiki/Fibonacci_number#Binet%27s_formula) kullanarak tam sayılar dışındaki değerlere genişletmek için.
  * **Doğruluk:** Tip bildirimleri, fonksiyonunuzun yalnızca belirli argüman türleri için doğru sonuçlar döndürmesi durumunda faydalı olabilir. Örneğin, argüman türlerini atlayıp `fib(n) = n ≤ 2 ? one(n) : fib(n-1) + fib(n-2)` yazsaydık, `fib(1.5)` sessizce mantıksız bir cevap olan `1.0` döndürecekti.
  * **Açıklık:** Tür bildirimleri, beklenen argümanlar hakkında bir belgeleme biçimi olarak hizmet edebilir.

Ancak, **argüman türlerini aşırı kısıtlamak yaygın bir hatadır**, bu da işlevin uygulanabilirliğini gereksiz yere sınırlayabilir ve beklemediğiniz durumlarda yeniden kullanılmasını engelleyebilir. Örneğin, yukarıdaki `fib(n::Integer)` işlevi `Int` argümanları (makine tam sayıları) ve `BigInt` rastgele hassasiyetli tam sayılar için eşit derecede iyi çalışır (bkz. [BigFloats and BigInts](@ref BigFloats-and-BigInts)), bu özellikle faydalıdır çünkü Fibonacci sayıları üssel olarak hızla büyür ve `Int` gibi sabit hassasiyetli türlerin herhangi birini hızla taşar (bkz. [Overflow behavior](@ref)). Ancak, işlevimizi `fib(n::Int)` olarak tanımlasaydık, `BigInt` uygulaması gereksiz yere engellenmiş olacaktı. Genel olarak, argümanlar için en genel uygulanabilir soyut türleri kullanmalısınız ve **şüphe durumunda, argüman türlerini atlayın**. Gerekirse daha sonra argüman türü spesifikasyonları ekleyebilirsiniz ve bunları atlayarak performans veya işlevsellikten ödün vermezsiniz.

## The `return` Keyword

Bir fonksiyonun döndürdüğü değer, değerlendirilen son ifadenin değeridir; bu, varsayılan olarak, fonksiyon tanımının gövdesindeki son ifadedir. Önceki bölümdeki örnek fonksiyon `f` için bu, `x + y` ifadesinin değeridir. Alternatif olarak, birçok diğer dilde olduğu gibi, `return` anahtar kelimesi bir fonksiyonun hemen döndürmesini sağlar ve döndürülen değeri sağlayan bir ifade sunar:

```julia
function g(x, y)
    return x * y
    x + y
end
```

Fonksiyon tanımları etkileşimli oturumlara girilebildiğinden, bu tanımları karşılaştırmak kolaydır:

```jldoctest
julia> f(x, y) = x + y
f (generic function with 1 method)

julia> function g(x, y)
           return x * y
           x + y
       end
g (generic function with 1 method)

julia> f(2, 3)
5

julia> g(2, 3)
6
```

Elbette, `g` gibi tamamen lineer bir fonksiyon gövdesinde `return` kullanımı anlamsızdır çünkü `x + y` ifadesi asla değerlendirilmez ve `return` ifadesini atlayarak fonksiyondaki son ifade olarak `x * y` yapabiliriz. Ancak diğer kontrol akışlarıyla birlikte `return` gerçekten faydalıdır. İşte, `x` ve `y` uzunluklarına sahip bir dik üçgenin hipotenüs uzunluğunu hesaplayan ve taşmayı önleyen bir fonksiyon:

```jldoctest
julia> function hypot(x, y)
           x = abs(x)
           y = abs(y)
           if x > y
               r = y/x
               return x*sqrt(1 + r*r)
           end
           if y == 0
               return zero(x)
           end
           r = x/y
           return y*sqrt(1 + r*r)
       end
hypot (generic function with 1 method)

julia> hypot(3, 4)
5.0
```

Bu işlevden dönecek üç olası geri dönüş noktası vardır; bu noktalar, `x` ve `y` değerlerine bağlı olarak üç farklı ifadenin değerlerini döndürmektedir. Son satırdaki `return` ifadesi, son ifade olduğu için atlanabilir.

### [Return type](@id man-functions-return-type)

Bir dönüş türü, `::` operatörünü kullanarak fonksiyon bildiriminde belirtilebilir. Bu, dönüş değerini belirtilen türe dönüştürür.

```jldoctest
julia> function g(x, y)::Int8
           return x * y
       end;

julia> typeof(g(1, 2))
Int8
```

Bu fonksiyon, `x` ve `y` türlerinden bağımsız olarak her zaman bir `Int8` döndürecektir. Dönüş türleri hakkında daha fazla bilgi için [Type Declarations](@ref)'ya bakın.

Dönüş türü bildirimleri Julia'da **nadiren kullanılır**: genel olarak, Julia'nın derleyicisinin dönüş türünü otomatik olarak çıkarabileceği "tip-istikrarlı" fonksiyonlar yazmalısınız. Daha fazla bilgi için [Performance Tips](@ref man-performance-tips) bölümüne bakın.

### Returning nothing

Fonksiyonların bir değer döndürmesine gerek yoksa (yalnızca bazı yan etkiler için kullanılan fonksiyonlar), Julia geleneği [`nothing`](@ref) değerini döndürmektir:

```julia
function printx(x)
    println("x = $x")
    return nothing
end
```

Bu bir *konvansiyon*dur, çünkü `nothing` bir Julia anahtar kelimesi değil, yalnızca `Nothing` türünde bir tekil nesnedir. Ayrıca, yukarıdaki `printx` fonksiyonu örneğinin yapay olduğunu fark edebilirsiniz, çünkü `println` zaten `nothing` döndürdüğünden, `return` satırı gereksizdir.

`return hiçbir şey` ifadesi için iki olası kısaltılmış form vardır. Bir yandan, `return` anahtar kelimesi, `hiçbir şey`i örtük olarak döndürdüğü için tek başına kullanılabilir. Öte yandan, fonksiyonlar son olarak değerlendirilen ifadelerini örtük olarak döndürdüğünden, `hiçbir şey` son ifade olduğunda tek başına kullanılabilir. `return hiçbir şey` ifadesinin `return` veya `hiçbir şey` ile karşılaştırıldığında tercih edilmesi, bir kodlama stilidir.

## Operators Are Functions

Julia'da, çoğu operatör, özel sözdizimi desteği olan işlevlerdir. (Özel değerlendirme semantiğine sahip operatörler, `&&` ve `||` gibi, istisnalardır. Bu operatörler, [Short-Circuit Evaluation](@ref) operatörün değerlendirilmesinden önce operandlarının değerlendirilmemesini gerektirdiğinden, işlev olamazlar.) Buna göre, diğer işlevlerde olduğu gibi, parantezli argüman listeleri kullanarak da uygulayabilirsiniz:

```jldoctest
julia> 1 + 2 + 3
6

julia> +(1, 2, 3)
6
```

Infix biçimi, işlev uygulama biçimiyle tam olarak eşdeğerdir - aslında, ilki işlev çağrısını üretmek için içsel olarak ayrıştırılır. Bu aynı zamanda, [`+`](@ref) ve [`*`](@ref) gibi operatörleri diğer işlev değerleriyle yapacağınız gibi atayabileceğiniz ve geçirebileceğiniz anlamına gelir:

```jldoctest
julia> f = +;

julia> f(1, 2, 3)
6
```

`f` adı altında, fonksiyon infiks notasyonu desteklememektedir.

## Operators With Special Names

Birkaç özel ifade, belirgin olmayan isimlere sahip fonksiyon çağrılarına karşılık gelir. Bunlar:

| Expression            | Calls                                    |
|:--------------------- |:---------------------------------------- |
| `[A B C ...]`         | [`hcat`](@ref)                           |
| `[A; B; C; ...]`      | [`vcat`](@ref)                           |
| `[A B; C D; ...]`     | [`hvcat`](@ref)                          |
| `[A; B;; C; D;; ...]` | [`hvncat`](@ref)                         |
| `A'`                  | [`adjoint`](@ref)                        |
| `A[i]`                | [`getindex`](@ref)                       |
| `A[i] = x`            | [`setindex!`](@ref)                      |
| `A.n`                 | [`getproperty`](@ref Base.getproperty)   |
| `A.n = x`             | [`setproperty!`](@ref Base.setproperty!) |

Not edin ki `[A; B;; C; D;; ...]` gibi ama iki ardışık `;`dan fazla olan ifadeler de `hvncat` çağrılarına karşılık gelir.

## [Anonymous Functions](@id man-anonymous-functions)

Julia'daki fonksiyonlar [first-class objects](https://en.wikipedia.org/wiki/First-class_citizen): değişkenlere atanabilir ve atandıkları değişken üzerinden standart fonksiyon çağrı sözdizimi kullanılarak çağrılabilir. Argüman olarak kullanılabilirler ve değer olarak döndürülebilirler. Ayrıca, bu sözdizimlerinden birini kullanarak isimsiz olarak da oluşturulabilirler:

```jldoctest
julia> x -> x^2 + 2x - 1
#1 (generic function with 1 method)

julia> function (x)
           x^2 + 2x - 1
       end
#3 (generic function with 1 method)
```

Her bir ifade, bir argüman `x` alan ve bu değerdeki polinomun `x^2 + 2x - 1` değerini döndüren bir fonksiyon oluşturur. Sonucun genel bir fonksiyon olduğunu, ancak ardışık numaralandırmaya dayalı olarak derleyici tarafından oluşturulmuş bir isimle geldiğini unutmayın.

Anonim fonksiyonların birincil kullanımı, diğer fonksiyonları argüman olarak alan fonksiyonlara geçiş yapmaktır. Klasik bir örnek [`map`](@ref)'dır; bu, bir fonksiyonu bir dizinin her bir değerine uygular ve sonuç değerlerini içeren yeni bir dizi döndürür:

```jldoctest
julia> map(round, [1.2, 3.5, 1.7])
3-element Vector{Float64}:
 1.0
 4.0
 2.0
```

Bu, [`map`](@ref)'ya ilk argüman olarak geçirebileceğiniz adlandırılmış bir fonksiyon etkisi varsa iyidir. Ancak, genellikle, kullanıma hazır, adlandırılmış bir fonksiyon mevcut değildir. Bu durumlarda, anonim fonksiyon yapısı, bir isim gerektirmeden tek kullanımlık bir fonksiyon nesnesi oluşturmayı kolaylaştırır:

```jldoctest
julia> map(x -> x^2 + 2x - 1, [1, 3, -1])
3-element Vector{Int64}:
  2
 14
 -2
```

Birden fazla argüman kabul eden anonim bir fonksiyon, `(x,y,z)->2x+y-z` sözdizimi kullanılarak yazılabilir.

Anonim fonksiyonlar için argüman türü bildirimleri, adlandırılmış fonksiyonlar için olduğu gibi çalışır; örneğin `x::Integer->2x`. Anonim bir fonksiyonun dönüş türü belirtilemez.

Sıfır argümanlı anonim bir fonksiyon `()->2+2` şeklinde yazılabilir. Argümanı olmayan bir fonksiyon fikri garip gelebilir, ancak bir sonucun önceden hesaplanamayacağı (veya hesaplanmaması gerektiği) durumlarda faydalıdır. Örneğin, Julia'nın mevcut zamanı saniye cinsinden döndüren sıfır argümanlı [`time`](@ref) fonksiyonu vardır ve bu nedenle `seconds = ()->round(Int, time())` ifadesi, bu zamanı en yakın tam sayıya yuvarlayarak döndüren bir anonim fonksiyondur ve `seconds` değişkenine atanmıştır. Bu anonim fonksiyon her çağrıldığında `seconds()` mevcut zaman hesaplanacak ve döndürülecektir.

## Tuples

Julia'da, işlev argümanları ve dönüş değerleri ile yakından ilişkili olan yerleşik bir veri yapısı olan *tuple* bulunmaktadır. Tuple, herhangi bir değeri tutabilen ancak değiştirilemeyen (yani *değişmez*) sabit uzunlukta bir konteynerdir. Tuple'lar virgüller ve parantezler ile oluşturulur ve indeksleme yoluyla erişilebilir:

```jldoctest
julia> (1, 1+1)
(1, 2)

julia> (1,)
(1,)

julia> x = (0.0, "hello", 6*7)
(0.0, "hello", 42)

julia> x[2]
"hello"
```

Bir uzunluk-1 demetinin bir virgül ile yazılması gerektiğini unutmayın, `(1,)`, çünkü `(1)` sadece parantez içine alınmış bir değerdir. `()` boş (uzunluk-0) demeti temsil eder.

## Named Tuples

Demetlerin bileşenleri isteğe bağlı olarak adlandırılabilir; bu durumda *adlandırılmış demet* oluşturulur:

```jldoctest
julia> x = (a=2, b=1+2)
(a = 2, b = 3)

julia> x[1]
2

julia> x.a
2
```

Adlandırılmış demetlerin alanlarına, nokta sözdizimi (`x.a`) kullanarak isimle erişilebilir; bunun yanı sıra normal dizinleme sözdizimi (`x[1]` veya `x[:a]`) de kullanılabilir.

## [Destructuring Assignment and Multiple Return Values](@id destructuring-assignment)

Bir virgülle ayrılmış değişkenler listesi (isteğe bağlı olarak parantez içinde) bir atamanın sol tarafında görünebilir: sağ taraftaki değer, her bir değişkene sırayla atama yapılarak *yapılandırılır*:

```jldoctest
julia> (a, b, c) = 1:3
1:3

julia> b
2
```

Sağdaki değer bir yineleyici olmalıdır (bkz. [Iteration interface](@ref man-interface-iteration)) en az soldaki değişken sayısı kadar uzun (yineleyicinin fazla elemanları göz ardı edilir).

Bu, bir tuple veya başka bir iterable değer döndürerek fonksiyonlardan birden fazla değer döndürmek için kullanılabilir. Örneğin, aşağıdaki fonksiyon iki değer döndürmektedir:

```jldoctest foofunc
julia> function foo(a, b)
           a+b, a*b
       end
foo (generic function with 1 method)
```

Eğer bunu bir etkileşimli oturumda geri dönüş değerini herhangi bir yere atamadan çağırırsanız, döndürülen demeti göreceksiniz:

```jldoctest foofunc
julia> foo(2, 3)
(5, 6)
```

Destructuring atama, her bir değeri bir değişkene çıkarır:

```jldoctest foofunc
julia> x, y = foo(2, 3)
(5, 6)

julia> x
5

julia> y
6
```

Başka bir yaygın kullanım, değişkenleri değiştirmektir:

```jldoctest foofunc
julia> y, x = x, y
(5, 6)

julia> x
6

julia> y
5
```

Eğer yalnızca yineleyicinin öğelerinin bir alt kümesine ihtiyaç varsa, göz ardı edilen öğeleri yalnızca alt çizgilerden `_` oluşan bir değişkene atamak yaygın bir uygulamadır (bu, aksi takdirde geçersiz bir değişken adı olan [Allowed Variable Names](@ref man-allowed-variable-names)'e bakın):

```jldoctest
julia> _, _, _, d = 1:10
1:10

julia> d
4
```

Diğer geçerli sol taraf ifadeleri, atama listesinin elemanları olarak kullanılabilir; bu, [`setindex!`](@ref) veya [`setproperty!`](@ref) çağıracak veya yinelemeciden bireysel öğeleri ayrıştıracaktır:

```jldoctest
julia> X = zeros(3);

julia> X[1], (a, b) = (1, (2, 3))
(1, (2, 3))

julia> X
3-element Vector{Float64}:
 1.0
 0.0
 0.0

julia> a
2

julia> b
3
```

!!! compat "Julia 1.6"
    `...` atama ile Julia 1.6 gerektirir


Eğer atama listesindeki son sembol `...` ile sonlandırılmışsa (bu duruma *slurping* denir), o zaman sağdaki iteratörün kalan elemanlarının bir koleksiyonu veya tembel bir iteratörü atanacaktır:

```jldoctest
julia> a, b... = "hello"
"hello"

julia> a
'h': ASCII/Unicode U+0068 (category Ll: Letter, lowercase)

julia> b
"ello"

julia> a, b... = Iterators.map(abs2, 1:4)
Base.Generator{UnitRange{Int64}, typeof(abs2)}(abs2, 1:4)

julia> a
1

julia> b
Base.Iterators.Rest{Base.Generator{UnitRange{Int64}, typeof(abs2)}, Int64}(Base.Generator{UnitRange{Int64}, typeof(abs2)}(abs2, 1:4), 1)
```

[`Base.rest`](@ref) hakkında belirli yineleyicilerin hassas işlenmesi ve özelleştirilmesi için ayrıntılar için bakın.

!!! compat "Julia 1.9"
    `...` atama ifadesinin sonu dışında kullanılması Julia 1.9 gerektirir


Atama atma görevlerinde de herhangi bir pozisyonda gerçekleşebilir. Ancak bir koleksiyonun sonunu yudumlamak yerine, bu her zaman hevesli olacaktır.

```jldoctest
julia> a, b..., c = 1:5
1:5

julia> a
1

julia> b
3-element Vector{Int64}:
 2
 3
 4

julia> c
5

julia> front..., tail = "Hi!"
"Hi!"

julia> front
"Hi"

julia> tail
'!': ASCII/Unicode U+0021 (category Po: Punctuation, other)
```

Bu, [`Base.split_rest`](@ref) fonksiyonu açısından uygulanmıştır.

Not edin ki, değişken sayıda argüman alan fonksiyon tanımlarında, slurping yalnızca son pozisyonda izin verilmektedir. Ancak bu, [single argument destructuring](@ref man-argument-destructuring) için geçerli değildir, çünkü bu yöntem dağıtımını etkilemez:

```jldoctest
julia> f(x..., y) = x
ERROR: syntax: invalid "..." on non-final argument
Stacktrace:
[...]

julia> f((x..., y)) = x
f (generic function with 1 method)

julia> f((1, 2, 3))
(1, 2)
```

## Property destructuring

Atama ayırma işlemi, yineleme yerine atamaların sağ tarafında da özellik adlarına göre yapılabilir. Bu, NamedTuples için kullanılan sözdizimini takip eder ve soldaki her değişkene, atamanın sağ tarafındaki aynı ada sahip bir özelliği `getproperty` kullanarak atayarak çalışır:

```jldoctest
julia> (; b, a) = (a=1, b=2, c=3)
(a = 1, b = 2, c = 3)

julia> a
1

julia> b
2
```

## [Argument destructuring](@id man-argument-destructuring)

Fonksiyon argümanı içinde de parçalama özelliği kullanılabilir. Eğer bir fonksiyon argümanı adı bir demet (örneğin `(x, y)`) olarak yazılırsa, o zaman `(x, y) = argüman` ataması sizin için eklenir:

```julia-repl
julia> minmax(x, y) = (y < x) ? (y, x) : (x, y)

julia> gap((min, max)) = max - min

julia> gap(minmax(10, 2))
8
```

`gap` tanımındaki ekstra parantez setine dikkat edin. O parantezler olmadan, `gap` iki argümanlı bir fonksiyon olurdu ve bu örnek çalışmazdı.

Benzer şekilde, nesne parçalama işlev argümanları için de kullanılabilir:

```julia-repl
julia> foo((; x, y)) = x + y
foo (generic function with 1 method)

julia> foo((x=1, y=2))
3

julia> struct A
           x
           y
       end

julia> foo(A(3, 4))
7
```

Anonim fonksiyonlar için, tek bir argümanı parçalamak ekstra bir virgül gerektirir:

```
julia> map(((x, y),) -> x + y, [(1, 2), (3, 4)])
2-element Array{Int64,1}:
 3
 7
```

## Varargs Functions

Genellikle, rastgele sayıda argüman alabilen fonksiyonlar yazmak kullanışlıdır. Bu tür fonksiyonlar geleneksel olarak "varargs" fonksiyonları olarak bilinir; bu, "değişken sayıda argüman" anlamına gelir. Bir varargs fonksiyonu, son konumsal argümandan sonra üç nokta (...) ekleyerek tanımlanabilir:

```jldoctest barfunc
julia> bar(a, b, x...) = (a, b, x)
bar (generic function with 1 method)
```

Değişkenler `a` ve `b`, her zamanki gibi ilk iki argüman değerine bağlanır ve değişken `x`, `bar` fonksiyonuna ilk iki argümandan sonra geçirilen sıfır veya daha fazla değerin iterable koleksiyonuna bağlanır:

```jldoctest barfunc
julia> bar(1, 2)
(1, 2, ())

julia> bar(1, 2, 3)
(1, 2, (3,))

julia> bar(1, 2, 3, 4)
(1, 2, (3, 4))

julia> bar(1, 2, 3, 4, 5, 6)
(1, 2, (3, 4, 5, 6))
```

Bu tüm durumlarda, `x`, `bar`'a geçirilen son değerlerin bir demetine bağlıdır.

Değişken argüman olarak geçirilen değerlerin sayısını sınırlamak mümkündür; bu, daha sonra [Parametrically-constrained Varargs methods](@ref) içinde tartışılacaktır.

Diğer taraftan, bir iterable koleksiyondaki değerleri bir fonksiyon çağrısına bireysel argümanlar olarak "splat" etmek genellikle kullanışlıdır. Bunu yapmak için, fonksiyon çağrısında da `...` kullanılır:

```jldoctest barfunc
julia> x = (3, 4)
(3, 4)

julia> bar(1, 2, x...)
(1, 2, (3, 4))
```

Bu durumda, bir değerler demeti, değişken sayıda argümanın gittiği yere tam olarak bir varargs çağrısına eklenir. Ancak bu durum geçerli olmak zorunda değildir:

```jldoctest barfunc
julia> x = (2, 3, 4)
(2, 3, 4)

julia> bar(1, x...)
(1, 2, (3, 4))

julia> x = (1, 2, 3, 4)
(1, 2, 3, 4)

julia> bar(x...)
(1, 2, (3, 4))
```

Ayrıca, bir işlev çağrısına yayılmış olan iterable nesnesi bir demet olmak zorunda değildir:

```jldoctest barfunc
julia> x = [3, 4]
2-element Vector{Int64}:
 3
 4

julia> bar(1, 2, x...)
(1, 2, (3, 4))

julia> x = [1, 2, 3, 4]
4-element Vector{Int64}:
 1
 2
 3
 4

julia> bar(x...)
(1, 2, (3, 4))
```

Ayrıca, argümanların yayılacağı fonksiyonun bir varargs fonksiyonu olması gerekmez (ancak genellikle öyledir):

```jldoctest
julia> baz(a, b) = a + b;

julia> args = [1, 2]
2-element Vector{Int64}:
 1
 2

julia> baz(args...)
3

julia> args = [1, 2, 3]
3-element Vector{Int64}:
 1
 2
 3

julia> baz(args...)
ERROR: MethodError: no method matching baz(::Int64, ::Int64, ::Int64)
The function `baz` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  baz(::Any, ::Any)
   @ Main none:1

Stacktrace:
[...]
```

Gördüğünüz gibi, eğer patlatılmış konteynerde yanlış sayıda eleman varsa, o zaman fonksiyon çağrısı başarısız olacaktır, tıpkı çok fazla argüman açıkça verildiğinde olduğu gibi.

## Optional Arguments

Fonksiyon argümanları için mantıklı varsayılan değerler sağlamak genellikle mümkündür. Bu, kullanıcıların her çağrıda her argümanı geçmek zorunda kalmalarını önleyebilir. Örneğin, [`Date(y, [m, d])`](@ref) fonksiyonu `Dates` modülünden, verilen bir yıl `y`, ay `m` ve gün `d` için bir `Date` türü oluşturur. Ancak, `m` ve `d` argümanları isteğe bağlıdır ve varsayılan değerleri `1`'dir. Bu davranış kısaca şöyle ifade edilebilir:

```jldoctest date_default_args
julia> using Dates

julia> function date(y::Int64, m::Int64=1, d::Int64=1)
           err = Dates.validargs(Date, y, m, d)
           err === nothing || throw(err)
           return Date(Dates.UTD(Dates.totaldays(y, m, d)))
       end
date (generic function with 3 methods)
```

Gözlemleyin ki, bu tanım `UTInstant{Day}` türünde bir argüman alan `Date` fonksiyonunun başka bir yöntemini çağırmaktadır.

Bu tanım ile, fonksiyon ya bir, ya iki ya da üç argüman ile çağrılabilir ve yalnızca bir veya iki argüman belirtildiğinde `1` otomatik olarak geçilir:

```jldoctest date_default_args
julia> date(2000, 12, 12)
2000-12-12

julia> date(2000, 12)
2000-12-01

julia> date(2000)
2000-01-01
```

Opsiyonel argümanlar, aslında farklı sayıda argümanla birden fazla yöntem tanımı yazmak için kullanışlı bir sözdizimidir (bkz. [Note on Optional and keyword Arguments](@ref)). Bu, `date` fonksiyonu örneğimiz için `methods` fonksiyonunu çağırarak kontrol edilebilir:

```julia-repl
julia> methods(date)
# 3 methods for generic function "date":
[1] date(y::Int64) in Main at REPL[1]:1
[2] date(y::Int64, m::Int64) in Main at REPL[1]:1
[3] date(y::Int64, m::Int64, d::Int64) in Main at REPL[1]:1
```

## Keyword Arguments

Bazı fonksiyonlar büyük sayıda argümana ihtiyaç duyar veya çok sayıda davranışa sahiptir. Bu tür fonksiyonları nasıl çağıracağınızı hatırlamak zor olabilir. Anahtar kelime argümanları, argümanların yalnızca konumla değil, adla tanımlanmasına izin vererek bu karmaşık arayüzlerin kullanılmasını ve genişletilmesini kolaylaştırabilir.

Örneğin, bir çizgi çizen `plot` adlı bir fonksiyonu düşünün. Bu fonksiyon, çizgi stili, genişliği, rengi ve benzeri şeyleri kontrol etmek için birçok seçeneğe sahip olabilir. Eğer anahtar kelime argümanlarını kabul ediyorsa, olası bir çağrı şöyle görünebilir: `plot(x, y, width=2)`, burada yalnızca çizgi genişliğini belirtmeyi seçmişiz. Bu durumun iki amacı vardır. Çağrı daha okunabilir hale gelir, çünkü bir argümanı anlamıyla etiketleyebiliriz. Ayrıca, büyük sayıda argümanın herhangi bir alt kümesini, herhangi bir sırayla geçmek mümkün hale gelir.

Anahtar kelime argümanları ile fonksiyonlar, imzada bir noktalı virgül kullanılarak tanımlanır:

```julia
function plot(x, y; style="solid", width=1, color="black")
    ###
end
```

Fonksiyon çağrıldığında, noktalı virgül isteğe bağlıdır: `plot(x, y, width=2)` veya `plot(x, y; width=2)` şeklinde çağrılabilir, ancak birinci stil daha yaygındır. Aşağıda açıklandığı gibi, yalnızca varargs veya hesaplanan anahtar kelimeleri geçerken açık bir noktalı virgül gereklidir.

Anahtar argüman varsayılan değerleri yalnızca gerekli olduğunda (karşılık gelen bir anahtar argüman geçilmediğinde) ve soldan sağa doğru değerlendirilir. Bu nedenle varsayılan ifadeler önceki anahtar argümanlara atıfta bulunabilir.

Anahtar argüman türleri aşağıdaki gibi açıkça belirtilebilir:

```julia
function f(; x::Int=1)
    ###
end
```

Anahtar argümanlar, varargs fonksiyonlarında da kullanılabilir:

```julia
function plot(x...; style="solid")
    ###
end
```

Ekstra anahtar kelime argümanları `...` kullanılarak toplanabilir, varargs fonksiyonlarında olduğu gibi:

```julia
function f(x; y=0, kwargs...)
    ###
end
```

`f` içinde, `kwargs` adlandırılmış bir demet üzerinde değiştirilemez bir anahtar-değer yineleyicisidir. Adlandırılmış demetler (ve `Symbol` anahtarlarına sahip sözlükler ile ilk değerleri sembol olan iki değerli koleksiyonlar üreten diğer yineleyiciler) bir çağrıda anahtar kelime argümanları olarak noktalı virgül kullanılarak geçirilebilir, örneğin `f(x, z=1; kwargs...)`.

Eğer bir anahtar kelime argümanı yöntem tanımında varsayılan bir değere atanmadıysa, o zaman *zorunludur*: çağıran bir değer atamazsa [`UndefKeywordError`](@ref) istisnası fırlatılacaktır:

```julia
function f(x; y)
    ###
end
f(3, y=5) # ok, y is assigned
f(3)      # throws UndefKeywordError(:y)
```

Bir nokta da noktalı virgülden sonra `anahtar => değer` ifadeleri geçirebilir. Örneğin, `plot(x, y; :width => 2)` ifadesi `plot(x, y, width=2)` ile eşdeğerdir. Bu, anahtar adının çalışma zamanında hesaplandığı durumlarda faydalıdır.

Bir çıplak tanımlayıcı veya nokta ifadesi bir noktalı virgülden sonra meydana geldiğinde, anahtar kelime argüman adı tanımlayıcı veya alan adı ile ima edilir. Örneğin `plot(x, y; width)` ifadesi `plot(x, y; width=width)` ile eşdeğerdir ve `plot(x, y; options.width)` ifadesi `plot(x, y; width=options.width)` ile eşdeğerdir.

Anahtar argümanların doğası, aynı argümanı birden fazla kez belirtmeyi mümkün kılar. Örneğin, `plot(x, y; options..., width=2)` çağrısında `options` yapısının da `width` için bir değer içermesi mümkündür. Bu durumda, en sağdaki örnek önceliğe sahiptir; bu örnekte, `width` kesinlikle `2` değerine sahip olacaktır. Ancak, aynı anahtar argümanı birden fazla kez açıkça belirtmek, örneğin `plot(x, y, width=2, width=3)`, izin verilmez ve bir sözdizimi hatasına yol açar.

## Evaluation Scope of Default Values

Seçenekli ve anahtar kelime argüman varsayılan ifadeleri değerlendirildiğinde, yalnızca *önceki* argümanlar kapsamda bulunur. Örneğin, bu tanım verildiğinde:

```julia
function f(x, a=b, b=1)
    ###
end
```

`a=b` ifadesindeki `b`, dış kapsamda bulunan bir `b`'ye atıfta bulunur, sonraki argüman `b`'ye değil.

## Do-Block Syntax for Function Arguments

Fonksiyonları diğer fonksiyonlara argüman olarak geçirmek güçlü bir tekniktir, ancak bunun için kullanılan sözdizimi her zaman pratik değildir. Bu tür çağrılar, fonksiyon argümanının birden fazla satır gerektirdiği durumlarda özellikle yazması zor hale gelir. Örneğin, [`map`](@ref) fonksiyonunu birkaç durumu olan bir fonksiyona çağırmayı düşünün:

```julia
map(x->begin
           if x < 0 && iseven(x)
               return 0
           elseif x == 0
               return 1
           else
               return x
           end
       end,
    [A, B, C])
```

Julia, bu kodu daha net bir şekilde yeniden yazmak için `do` adlı bir ayrılmış kelime sağlar:

```julia
map([A, B, C]) do x
    if x < 0 && iseven(x)
        return 0
    elseif x == 0
        return 1
    else
        return x
    end
end
```

`do x` sözdizimi, `x` argümanına sahip bir anonim fonksiyon oluşturur ve anonim fonksiyonu "dış" fonksiyona ilk argüman olarak geçirir - bu örnekte [`map`](@ref). Benzer şekilde, `do a,b` iki argümanlı bir anonim fonksiyon oluşturur. `do (a,b)` ifadesinin bir argümanlı bir anonim fonksiyon oluşturduğunu, argümanının bir demet olduğunu unutmayın. Sade bir `do`, ardından gelenin `() -> ...` biçiminde bir anonim fonksiyon olduğunu belirtir.

Bu argümanların nasıl başlatıldığı "dış" fonksiyona bağlıdır; burada, [`map`](@ref) sırasıyla `x`'i `A`, `B`, `C` olarak ayarlayacak ve her birinde anonim fonksiyonu çağıracaktır, tıpkı `map(func, [A, B, C])` sözdiziminde olduğu gibi.

Bu sözdizimi, işlevleri etkili bir şekilde dilin genişletilmesi için kullanmayı kolaylaştırır, çünkü çağrılar normal kod blokları gibi görünür. [`map`](@ref) gibi sistem durumunu yönetmek gibi oldukça farklı birçok olası kullanım vardır. Örneğin, açılan dosyanın sonunda kapatılmasını sağlayan bir [`open`](@ref) sürümü vardır:

```julia
open("outfile", "w") do io
    write(io, data)
end
```

Bu, aşağıdaki tanım ile gerçekleştirilir:

```julia
function open(f::Function, args...)
    io = open(args...)
    try
        f(io)
    finally
        close(io)
    end
end
```

Burada, [`open`](@ref) önce dosyayı yazma için açar ve ardından elde edilen çıktı akışını `do ... end` bloğunda tanımladığınız anonim fonksiyona geçirir. Fonksiyonunuzdan çıkıldığında, `4d61726b646f776e2e436f64652822222c20226f70656e2229_40726566` akışın düzgün bir şekilde kapatılmasını sağlar; bu, fonksiyonunuzun normal bir şekilde çıkıp çıkmadığına veya bir istisna fırlatıp fırlatmadığına bakılmaksızın gerçekleşir. (`try/finally` yapısı [Control Flow](@ref)'da açıklanacaktır.)

`do` bloğu sözdizimi ile, kullanıcı fonksiyonunun argümanlarının nasıl başlatıldığını bilmek için belgeleri veya uygulamayı kontrol etmek faydalıdır.

Bir `do` bloğu, diğer iç işlevler gibi, kapsayıcı kapsamından değişkenleri "yakalayabilir". Örneğin, `open...do` örneğinde yukarıda belirtilen `data` değişkeni dış kapsamdan yakalanır. Yakalanan değişkenler, [performance tips](@ref man-performance-captured) üzerinde tartışıldığı gibi performans zorlukları yaratabilir.

## Function composition and piping

Julia'da fonksiyonlar, birleştirilerek veya boru hattı (zincirleme) ile bir araya getirilebilir.

Fonksiyon bileşimi, fonksiyonları bir araya getirip elde edilen bileşimi argümanlara uyguladığınızda ortaya çıkar. Fonksiyon bileşimi operatörünü (`∘`) kullanarak fonksiyonları birleştirirsiniz, bu nedenle `(f ∘ g)(args...; kw...)` ifadesi `f(g(args...; kw...))` ile aynıdır.

REPL'de ve uygun şekilde yapılandırılmış editörlerde bileşim operatörünü `\circ<tab>` yazarak yazabilirsiniz.

Örneğin, `sqrt` ve `+` fonksiyonları şu şekilde birleştirilebilir:

```jldoctest
julia> (sqrt ∘ +)(3, 6)
3.0
```

Bu önce sayıları toplar, ardından sonucun karekökünü bulur.

Sonraki örnek, üç fonksiyonu birleştirir ve sonucu bir dizi dize üzerinde haritalar:

```jldoctest
julia> map(first ∘ reverse ∘ uppercase, split("you can compose functions like this"))
6-element Vector{Char}:
 'U': ASCII/Unicode U+0055 (category Lu: Letter, uppercase)
 'N': ASCII/Unicode U+004E (category Lu: Letter, uppercase)
 'E': ASCII/Unicode U+0045 (category Lu: Letter, uppercase)
 'S': ASCII/Unicode U+0053 (category Lu: Letter, uppercase)
 'E': ASCII/Unicode U+0045 (category Lu: Letter, uppercase)
 'S': ASCII/Unicode U+0053 (category Lu: Letter, uppercase)
```

Fonksiyon zincirleme (bazen "borulama" veya verileri bir sonraki fonksiyona göndermek için "bir boru kullanma" olarak adlandırılır) bir fonksiyonu önceki fonksiyonun çıktısına uyguladığınızda gerçekleşir:

```jldoctest
julia> 1:10 |> sum |> sqrt
7.416198487095663
```

Burada, `sum` tarafından üretilen toplam `sqrt` fonksiyonuna geçirilir. Eşdeğer bileşim şöyle olur:

```jldoctest
julia> (sqrt ∘ sum)(1:10)
7.416198487095663
```

Borulma operatörü, aşağıda açıklanan zincirleme/borulama ve nokta vektörleştirme sözdiziminin faydalı bir kombinasyonunu sağlamak için yayınlama ile de kullanılabilir, yani `.|>`.

```jldoctest
julia> ["a", "list", "of", "strings"] .|> [uppercase, reverse, titlecase, length]
4-element Vector{Any}:
  "A"
  "tsil"
  "Of"
 7
```

Anonim fonksiyonlarla boruları birleştirirken, sonraki boruların anonim fonksiyonun gövdesinin bir parçası olarak yorumlanmaması için parantez kullanılmalıdır. Karşılaştır:

```jldoctest
julia> 1:3 .|> (x -> x^2) |> sum |> sqrt
3.7416573867739413

julia> 1:3 .|> x -> x^2 |> sum |> sqrt
3-element Vector{Float64}:
 1.0
 2.0
 3.0
```

## [Dot Syntax for Vectorizing Functions](@id man-vectorized)

Teknik hesaplama dillerinde, bir dizinin her bir elemanına `f(x)` fonksiyonunu uygulayan "vektörleştirilmiş" fonksiyonların bulunması yaygındır ve bu, `f(A)` ile yeni bir dizi elde etmek için kullanılır. Bu tür bir sözdizimi veri işleme için kullanışlıdır, ancak diğer dillerde performans için de vektörleştirme sıklıkla gereklidir: döngüler yavaşsa, bir fonksiyonun "vektörleştirilmiş" versiyonu, düşük seviyeli bir dilde yazılmış hızlı kütüphane kodunu çağırabilir. Julia'da, vektörleştirilmiş fonksiyonlar performans için *zorunlu* değildir ve aslında kendi döngülerinizi yazmak genellikle faydalıdır (bkz. [Performance Tips](@ref man-performance-tips)), ancak yine de kullanışlı olabilirler. Bu nedenle, *herhangi bir* Julia fonksiyonu `f`, `f.(A)` sözdizimi ile herhangi bir diziye (veya diğer koleksiyonlara) eleman bazında uygulanabilir. Örneğin, `sin` fonksiyonu, `A` vektöründeki tüm elemanlara şu şekilde uygulanabilir:

```jldoctest
julia> A = [1.0, 2.0, 3.0]
3-element Vector{Float64}:
 1.0
 2.0
 3.0

julia> sin.(A)
3-element Vector{Float64}:
 0.8414709848078965
 0.9092974268256817
 0.1411200080598672
```

Elbette, `f`'nin özel bir "vektör" yöntemini yazarsanız noktayı atlayabilirsiniz, örneğin `f(A::AbstractArray) = map(f, A)` şeklinde ve bu, `f.(A)` kadar verimlidir. `f.(A)` sözdiziminin avantajı, hangi fonksiyonların vektörleştirilebilir olduğunun kütüphane yazarı tarafından önceden belirlenmesine gerek olmamasıdır.

Daha genel olarak, `f.(args...)` aslında `broadcast(f, args...)` ile eşdeğerdir; bu, birden fazla dizi (hatta farklı şekillerde) veya diziler ve skalarların karışımı üzerinde işlem yapmanıza olanak tanır (bkz. [Broadcasting](@ref)). Örneğin, `f(x, y) = 3x + 4y` ifadesine sahipseniz, `f.(pi, A)` ifadesi, `A` içindeki her `a` için `f(pi,a)` değerlerinden oluşan yeni bir dizi döndürecektir ve `f.(vector1, vector2)` ifadesi, her `i` indeksi için `f(vector1[i], vector2[i])` değerlerinden oluşan yeni bir vektör döndürecektir (vektörler farklı uzunlukta ise bir istisna fırlatır).

```jldoctest
julia> f(x, y) = 3x + 4y;

julia> A = [1.0, 2.0, 3.0];

julia> B = [4.0, 5.0, 6.0];

julia> f.(pi, A)
3-element Vector{Float64}:
 13.42477796076938
 17.42477796076938
 21.42477796076938

julia> f.(A, B)
3-element Vector{Float64}:
 19.0
 26.0
 33.0
```

Anahtar argümanlar yayılmıyor, ancak her fonksiyon çağrısına basitçe iletiliyor. Örneğin, `round.(x, digits=3)` ifadesi `broadcast(x -> round(x, digits=3), x)` ile eşdeğerdir.

Ayrıca, *iç içe* `f.(args...)` çağrıları tek bir `broadcast` döngüsünde *birleştirilir*. Örneğin, `sin.(cos.(X))` ifadesi `broadcast(x -> sin(cos(x)), X)` ile eşdeğerdir, bu da `[sin(cos(x)) for x in X]` ile benzerdir: `X` üzerinde yalnızca tek bir döngü vardır ve sonuç için tek bir dizi tahsis edilir. [Buna karşılık, tipik bir "vektörleştirilmiş" dilde `sin(cos(X))` ifadesi önce `tmp=cos(X)` için bir geçici dizi tahsis eder ve ardından `sin(tmp)`'yi ayrı bir döngüde hesaplayarak ikinci bir dizi tahsis eder.] Bu döngü birleştirmesi, gerçekleşip gerçekleşmeyeceği bir derleyici optimizasyonu değildir, iç içe `f.(args...)` çağrılarıyla karşılaşıldığında her zaman bir *sentaktik garanti* vardır. Teknik olarak, bir "nokta olmayan" fonksiyon çağrısı ile karşılaşıldığında birleştirme durur; örneğin, `sin.(sort(cos.(X)))` ifadesinde `sin` ve `cos` döngüleri, araya giren `sort` fonksiyonu nedeniyle birleştirilemez.

Sonunda, maksimum verim genellikle bir vektörleştirilmiş işlemin çıktı dizisi *önceden ayrıldığında* elde edilir, böylece tekrar eden çağrılar sonuçlar için yeni diziler ayırmaz (bkz. [Pre-allocating outputs](@ref)). Bunun için kullanışlı bir sözdizimi `X .= ...` şeklindedir; bu, `broadcast!(identity, X, ...)` ile eşdeğerdir, ancak yukarıda olduğu gibi, `broadcast!` döngüsü herhangi bir iç içe "nokta" çağrılarıyla birleştirilmiştir. Örneğin, `X .= sin.(Y)` ifadesi `broadcast!(sin, X, Y)` ile eşdeğerdir ve `X`'i `sin.(Y)` ile yerinde günceller. Eğer sol taraf bir dizi indeksleme ifadesiyse, örneğin `X[begin+1:end] .= sin.(Y)`, bu `view` üzerinde `broadcast!` olarak çevrilir; örneğin, `broadcast!(sin, view(X, firstindex(X)+1:lastindex(X)), Y)` şeklindedir, böylece sol taraf yerinde güncellenir.

Nokta ekleme işlemleri ve bir ifadede fonksiyon çağrıları, kodun okunmasını zorlaştıracak şekilde zahmetli olabileceğinden, her bir fonksiyon çağrısını, işlemi ve atamayı "noktalı" versiyonuna dönüştürmek için [`@.`](@ref @__dot__) makrosu sağlanmıştır.

```jldoctest
julia> Y = [1.0, 2.0, 3.0, 4.0];

julia> X = similar(Y); # pre-allocate output array

julia> @. X = sin(cos(Y)) # equivalent to X .= sin.(cos.(Y))
4-element Vector{Float64}:
  0.5143952585235492
 -0.4042391538522658
 -0.8360218615377305
 -0.6080830096407656
```

İkili (veya tekil) operatörler, `.+` gibi, aynı mekanizma ile işlenir: bunlar `broadcast` çağrıları ile eşdeğerdir ve diğer iç içe "nokta" çağrıları ile birleştirilir. `X .+= Y` vb. ifadeleri, `X .= X .+ Y` ile eşdeğerdir ve birleştirilmiş yerinde atama ile sonuçlanır; ayrıca bkz. [dot operators](@ref man-dot-operators).

Ayrıca, bu örnekte olduğu gibi [`|>`](@ref) kullanarak nokta işlemlerini fonksiyon zincirleme ile birleştirebilirsiniz:

```jldoctest
julia> 1:5 .|> [x->x^2, inv, x->2*x, -, isodd]
5-element Vector{Real}:
    1
    0.5
    6
   -4
 true
```

Tüm birleşik yayılmadaki fonksiyonlar, sonucun her bir elemanı için her zaman çağrılır. Bu nedenle `X .+ σ .* randn.()` ifadesi, dizi `X`'nin her bir elemanına bağımsız ve aynı şekilde örneklenmiş rastgele değerler ekleyecektir, ancak `X .+ σ .* randn()` ifadesi her bir elemana *aynı* rastgele örneği ekleyecektir. Birleşik hesaplamanın yayılma yinelemesinin bir veya daha fazla eksen boyunca sabit olduğu durumlarda, ara değerleri tahsis ederek hesaplama sayısını azaltmak için bir alan-zaman takası kullanmak mümkün olabilir. Daha fazla bilgi için [performance tips](@ref man-performance-unfuse) adresine bakın.

## Further Reading

Burada belirtmemiz gerekir ki, bu, fonksiyonları tanımlamanın tamamlayıcı bir resmi değildir. Julia, karmaşık bir tür sistemine sahiptir ve argüman türleri üzerinde çoklu dağıtım (multiple dispatch) yapılmasına olanak tanır. Burada verilen örneklerin hiçbiri argümanları üzerinde herhangi bir tür açıklaması sağlamamaktadır, bu da onların tüm argüman türlerine uygulanabilir olduğu anlamına gelir. Tür sistemi [Types](@ref man-types) içinde tanımlanmıştır ve bir fonksiyonu çalışma zamanı argüman türlerine göre seçilen yöntemler ile tanımlamak [Methods](@ref) içinde açıklanmaktadır.
