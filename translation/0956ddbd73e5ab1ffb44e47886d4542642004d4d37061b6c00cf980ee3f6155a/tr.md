# Metaprogramming

Lisp'in Julia dilindeki en güçlü mirası, metaprogramlama desteğidir. Lisp gibi, Julia da kendi kodunu dilin kendisine ait bir veri yapısı olarak temsil eder. Kod, dilin içinden oluşturulup manipüle edilebilen nesnelerle temsil edildiğinden, bir program kendi kodunu dönüştürüp oluşturabilir. Bu, ek derleme adımları olmadan karmaşık kod üretimine olanak tanır ve ayrıca [abstract syntax trees](https://en.wikipedia.org/wiki/Abstract_syntax_tree) seviyesinde çalışan gerçek Lisp tarzı makrolara da olanak tanır. Buna karşılık, C ve C++ gibi ön işleyici "makro" sistemleri, herhangi bir gerçek ayrıştırma veya yorumlama gerçekleşmeden önce metin manipülasyonu ve yer değiştirme işlemleri gerçekleştirir. Julia'daki tüm veri türleri ve kod, Julia veri yapılarıyla temsil edildiğinden, bir programın ve türlerinin iç yapısını keşfetmek için güçlü [reflection](https://en.wikipedia.org/wiki/Reflection_%28computer_programming%29) yetenekleri mevcuttur.

!!! warning
    Metaprogramming, güçlü bir araçtır, ancak kodun anlaşılmasını zorlaştırabilecek karmaşıklıklar getirir. Örneğin, kapsam kurallarını doğru bir şekilde almak şaşırtıcı derecede zor olabilir. Metaprogramlama genellikle, [higher order functions](@ref man-anonymous-functions) ve [closures](https://en.wikipedia.org/wiki/Closure_(computer_programming)) gibi diğer yaklaşımlar uygulanamadığında kullanılmalıdır.

    `eval` ve yeni makrolar tanımlamak genellikle son çare olarak kullanılmalıdır. `Meta.parse` kullanmak veya rastgele bir dizeyi Julia koduna dönüştürmek neredeyse asla iyi bir fikir değildir. Julia kodunu manipüle etmek için, Julia sözdiziminin nasıl ayrıştırıldığının karmaşıklığından kaçınmak için `Expr` veri yapısını doğrudan kullanın.

    Metaprogramlamanın en iyi kullanımları genellikle işlevselliğinin çoğunu çalışma zamanı yardımcı işlevlerinde uygular ve ürettiği kod miktarını en aza indirmeye çalışır.


## Program representation

Herhangi bir Julia programı bir dize olarak başlar:

```jldoctest prog
julia> prog = "1 + 1"
"1 + 1"
```

**Sonra ne olacak?**

Sonraki adım, her dizeyi [parse](https://en.wikipedia.org/wiki/Parsing#Computer_languages) bir ifade olarak adlandırılan bir nesneye dönüştürmektir; bu ifade Julia türü [`Expr`](@ref) ile temsil edilir:

```jldoctest prog
julia> ex1 = Meta.parse(prog)
:(1 + 1)

julia> typeof(ex1)
Expr
```

`Expr` nesneleri iki bölüm içerir:

  * bir [`Symbol`](@ref) ifadenin türünü tanımlıyor. Bir sembol, [interned string](https://en.wikipedia.org/wiki/String_interning) tanımlayıcıdır (aşağıda daha fazla tartışma).

```jldoctest prog
julia> ex1.head
:call
```

  * ifade argümanları, semboller, diğer ifadeler veya literal değerler olabilir:

```jldoctest prog
julia> ex1.args
3-element Vector{Any}:
  :+
 1
 1
```

İfadeler doğrudan [prefix notation](https://en.wikipedia.org/wiki/Polish_notation) içinde de oluşturulabilir:

```jldoctest prog
julia> ex2 = Expr(:call, :+, 1, 1)
:(1 + 1)
```

Yukarıda oluşturulan iki ifade - ayrıştırma ile ve doğrudan yapı ile - eşdeğerdir:

```jldoctest prog
julia> ex1 == ex2
true
```

**Buradaki ana nokta, Julia kodunun dilin kendisinden erişilebilen bir veri yapısı olarak içsel olarak temsil edilmesidir.**

[`dump`](@ref) fonksiyonu `Expr` nesnelerinin girintili ve açıklamalı bir şekilde görüntülenmesini sağlar:

```jldoctest prog
julia> dump(ex2)
Expr
  head: Symbol call
  args: Array{Any}((3,))
    1: Symbol +
    2: Int64 1
    3: Int64 1
```

`Expr` nesneleri de iç içe olabilir:

```jldoctest ex3
julia> ex3 = Meta.parse("(4 + 4) / 2")
:((4 + 4) / 2)
```

Başka bir ifadeyi görüntülemenin bir yolu `Meta.show_sexpr` kullanmaktır; bu, verilen bir `Expr`'in [S-expression](https://en.wikipedia.org/wiki/S-expression) biçimini gösterir. Bu, Lisp kullanıcıları için oldukça tanıdık görünebilir. İşte iç içe bir `Expr` üzerindeki görüntüyü gösteren bir örnek:

```jldoctest ex3
julia> Meta.show_sexpr(ex3)
(:call, :/, (:call, :+, 4, 4), 2)
```

### Symbols

`:` karakterinin Julia'da iki sözdizimsel amacı vardır. İlk form, geçerli tanımlayıcılardan bir ifade yapı taşlarından biri olarak kullanılan bir [`Symbol`](@ref), bir [interned string](https://en.wikipedia.org/wiki/String_interning) oluşturur:

```jldoctest
julia> s = :foo
:foo

julia> typeof(s)
Symbol
```

[`Symbol`](@ref) yapıcısı, herhangi bir sayıda argümanı alır ve bunların string temsillerini birleştirerek yeni bir sembol oluşturur:

```jldoctest
julia> :foo === Symbol("foo")
true

julia> Symbol("1foo") # `:1foo` would not work, as `1foo` is not a valid identifier
Symbol("1foo")

julia> Symbol("func",10)
:func10

julia> Symbol(:var,'_',"sym")
:var_sym
```

Bir ifadenin bağlamında, semboller değişkenlere erişimi göstermek için kullanılır; bir ifade değerlendirildiğinde, bir sembol, o sembole bağlı olan değerle değiştirilir uygun [scope](@ref scope-of-variables) içinde.

Bazen `:` için argümanın etrafında ekstra parantezler, ayrıştırmada belirsizliği önlemek için gereklidir:

```jldoctest
julia> :(:)
:(:)

julia> :(::)
:(::)
```

## Expressions and evaluation

### Quoting

`:` karakterinin ikinci sözdizimsel amacı, açık [`Expr`](@ref) yapıcısını kullanmadan ifade nesneleri oluşturmaktır. Bu *alıntı* olarak adlandırılır. `:` karakteri, Julia kodunun tek bir ifadesinin etrafında çift parantez ile birlikte geldiğinde, kapsanan koda dayalı bir `Expr` nesnesi üretir. İşte bir aritmetik ifadeyi alıntılamak için kullanılan kısa formun bir örneği:

```jldoctest
julia> ex = :(a+b*c+1)
:(a + b * c + 1)

julia> typeof(ex)
Expr
```

(bu ifadenin yapısını görmek için `ex.head` ve `ex.args` komutlarını deneyin veya yukarıda olduğu gibi [`dump`](@ref) veya [`Meta.@dump`](@ref) kullanın)

Not edin ki eşdeğer ifadeler [`Meta.parse`](@ref) veya doğrudan `Expr` biçimi kullanılarak oluşturulabilir:

```jldoctest
julia>      :(a + b*c + 1)       ==
       Meta.parse("a + b*c + 1") ==
       Expr(:call, :+, :a, Expr(:call, :*, :b, :c), 1)
true
```

Parser tarafından sağlanan ifadeler genellikle yalnızca semboller, diğer ifadeler ve literal değerler argümanları olarak bulundururken, Julia kodu tarafından oluşturulan ifadeler, literal formlar olmadan rastgele çalışma zamanı değerlerine argüman olarak sahip olabilir. Bu özel örnekte, `+` ve `a` sembollerdir, `*(b,c)` bir alt ifadedir ve `1` bir literal 64-bit işaretli tam sayıdır.

Birden fazla ifade için ikinci bir sözdizim biçimi vardır: `quote ... end` ile kapsanan kod blokları.

```jldoctest
julia> ex = quote
           x = 1
           y = 2
           x + y
       end
quote
    #= none:2 =#
    x = 1
    #= none:3 =#
    y = 2
    #= none:4 =#
    x + y
end

julia> typeof(ex)
Expr
```

### [Interpolation](@id man-expression-interpolation)

[`Expr`](@ref) nesnelerinin değer argümanları ile doğrudan inşası güçlüdür, ancak `Expr` yapıcıları "normal" Julia sözdizimine kıyasla zahmetli olabilir. Alternatif olarak, Julia, alıntılanmış ifadelere literallerin veya ifadelerin *interpolasyonuna* izin verir. Interpolasyon, bir ön ek `$` ile belirtilir.

Bu örnekte, `a` değişkeninin değeri iç içe geçirilmiştir:

```jldoctest interp1
julia> a = 1;

julia> ex = :($a + b)
:(1 + b)
```

Bir alıntı yapılmamış ifadeye interpolasyon yapmak desteklenmiyor ve derleme zamanı hatasına neden olacaktır:

```jldoctest interp1
julia> $a + b
ERROR: syntax: "$" expression outside quote
```

Bu örnekte, `(1,2,3)` demetinin bir koşul testine ifade olarak yerleştirildiği gösterilmektedir:

```jldoctest interp1
julia> ex = :(a in $:((1,2,3)) )
:(a in (1, 2, 3))
```

`$` ifadesinin interpolasyonu için kullanımı, [string interpolation](@ref string-interpolation) ve [command interpolation](@ref command-interpolation) ile kasıtlı olarak benzerlik göstermektedir. İfade interpolasyonu, karmaşık Julia ifadelerinin programatik olarak kolay ve okunabilir bir şekilde oluşturulmasını sağlar.

### Splatting interpolation

Dikkat edin ki, `$` interpolasyon sözdizimi yalnızca bir tek ifadeyi çevreleyen ifadeye eklemeye izin verir. Bazen, bir dizi ifade ile karşılaşırsınız ve bunların hepsinin çevreleyen ifadenin argümanları haline gelmesi gerekir. Bu, `$(xs...)` sözdizimi ile yapılabilir. Örneğin, aşağıdaki kod, argüman sayısının programatik olarak belirlendiği bir fonksiyon çağrısı oluşturur:

```jldoctest interp1
julia> args = [:x, :y, :z];

julia> :(f(1, $(args...)))
:(f(1, x, y, z))
```

### Nested quote

Doğal olarak, alıntı ifadelerinin diğer alıntı ifadelerini içermesi mümkündür. Bu durumlarda interpolasyonun nasıl çalıştığını anlamak biraz zor olabilir. Bu örneği düşünün:

```jldoctest interp1
julia> x = :(1 + 2);

julia> e = quote quote $x end end
quote
    #= none:1 =#
    $(Expr(:quote, quote
    #= none:1 =#
    $(Expr(:$, :x))
end))
end
```

Sonuçta `$x` bulunduğunu unutmayın, bu da `x`'in henüz değerlendirilmediği anlamına gelir. Başka bir deyişle, `$` ifadesi "içteki alıntı ifadesine aittir" ve bu nedenle argümanı yalnızca içteki alıntı ifadesi değerlendirildiğinde:

```jldoctest interp1
julia> eval(e)
quote
    #= none:1 =#
    1 + 2
end
```

Ancak, dıştaki `quote` ifadesi, içteki alıntıdaki `$` içindeki değerleri ara katman olarak yerleştirebilir. Bu, birden fazla `$` ile yapılır:

```jldoctest interp1
julia> e = quote quote $$x end end
quote
    #= none:1 =#
    $(Expr(:quote, quote
    #= none:1 =#
    $(Expr(:$, :(1 + 2)))
end))
end
```

Dikkat edin ki `(1 + 2)` artık sonuçta `x` sembolü yerine görünmektedir. Bu ifadenin değerlendirilmesi, interpolasyon edilmiş bir `3` sonucunu verir:

```jldoctest interp1
julia> eval(e)
quote
    #= none:1 =#
    3
end
```

Bu davranışın arkasındaki sezgi, `x`'in her bir `$` için bir kez değerlendirildiğidir: bir `$`, `eval(:x)` ile benzer şekilde çalışarak `x`'in değerini verirken, iki `$`, `eval(eval(:x))`'in eşdeğerini yapar.

### [QuoteNode](@id man-quote-node)

`quote` form'un AST'deki yaygın temsili [`Expr`](@ref) olup başlığı `:quote`'dır:

```jldoctest interp1
julia> dump(Meta.parse(":(1+2)"))
Expr
  head: Symbol quote
  args: Array{Any}((1,))
    1: Expr
      head: Symbol call
      args: Array{Any}((3,))
        1: Symbol +
        2: Int64 1
        3: Int64 2
```

Gördüğümüz gibi, bu tür ifadeler `$` ile interpolasyonu destekler. Ancak, bazı durumlarda kodu *interpolasyon yapmadan* alıntılamak gereklidir. Bu tür bir alıntılamanın henüz bir sözdizimi yoktur, ancak dahili olarak `QuoteNode` türünde bir nesne olarak temsil edilir:

```jldoctest interp1
julia> eval(Meta.quot(Expr(:$, :(1+2))))
3

julia> eval(QuoteNode(Expr(:$, :(1+2))))
:($(Expr(:$, :(1 + 2))))
```

Parçacı, semboller gibi basit alıntılanmış öğeler için `QuoteNode`'lar üretir:

```jldoctest interp1
julia> dump(Meta.parse(":x"))
QuoteNode
  value: Symbol x
```

`QuoteNode`, belirli ileri düzey metaprogramlama görevleri için de kullanılabilir.

### Evaluating expressions

Verilen bir ifade nesnesi ile, Julia'nın bunu global kapsamda değerlendirmesini (çalıştırmasını) sağlamak için [`eval`](@ref) kullanabilirsiniz:

```jldoctest interp1
julia> ex1 = :(1 + 2)
:(1 + 2)

julia> eval(ex1)
3

julia> ex = :(a + b)
:(a + b)

julia> eval(ex)
ERROR: UndefVarError: `b` not defined in `Main`
[...]

julia> a = 1; b = 2;

julia> eval(ex)
3
```

Her [module](@ref modules) kendi [`eval`](@ref) fonksiyonuna sahiptir ve bu fonksiyon ifadeleri küresel kapsamda değerlendirir. `4d61726b646f776e2e436f64652822222c20226576616c2229_40726566`'ya geçirilen ifadeler yalnızca değer döndürmekle sınırlı değildir - aynı zamanda kapsayıcı modülün ortamının durumunu değiştiren yan etkileri de olabilir:

```jldoctest
julia> ex = :(x = 1)
:(x = 1)

julia> x
ERROR: UndefVarError: `x` not defined in `Main`

julia> eval(ex)
1

julia> x
1
```

Burada, bir ifade nesnesinin değerlendirilmesi, `x` küresel değişkenine bir değer atanmasına neden olur.

İfadeler, programatik olarak oluşturulabilen ve ardından değerlendirilebilen `Expr` nesneleridir, bu nedenle dinamik olarak rastgele kod oluşturmak ve ardından [`eval`](@ref) kullanarak çalıştırmak mümkündür. İşte basit bir örnek:

```julia-repl
julia> a = 1;

julia> ex = Expr(:call, :+, a, :b)
:(1 + b)

julia> a = 0; b = 2;

julia> eval(ex)
3
```

`a` değerinin, 1 ve `b` değişkenine `+` fonksiyonunu uygulayan `ex` ifadesini oluşturmak için kullanıldığı belirtilmiştir. `a` ve `b`'nin kullanım şekilleri arasındaki önemli farkı not edin:

  * Değişken `a`nın ifade oluşturma zamanındaki değeri, ifadede anlık bir değer olarak kullanılır. Bu nedenle, ifadenin değerlendirildiği zaman `a`nın değeri artık önemli değildir: ifadede yer alan değer zaten `1`dir, `a`nın olası değeri ne olursa olsun.
  * Diğer yandan, *sembol* `:b` ifade inşasında kullanılır, bu nedenle o anda `b` değişkeninin değeri önemsizdir - `:b` sadece bir semboldür ve `b` değişkeninin tanımlanması bile gerekmez. Ancak ifade değerlendirme zamanında, `:b` sembolünün değeri `b` değişkeninin değerini arayarak çözülür.

### Functions on `Expr`essions

As hinted above, one extremely useful feature of Julia is the capability to generate and manipulate Julia code within Julia itself. We have already seen one example of a function returning [`Expr`](@ref) objects: the [`Meta.parse`](@ref) function, which takes a string of Julia code and returns the corresponding `Expr`. A function can also take one or more `Expr` objects as arguments, and return another `Expr`. Here is a simple, motivating example:

```jldoctest
julia> function math_expr(op, op1, op2)
           expr = Expr(:call, op, op1, op2)
           return expr
       end
math_expr (generic function with 1 method)

julia>  ex = math_expr(:+, 1, Expr(:call, :*, 4, 5))
:(1 + 4 * 5)

julia> eval(ex)
21
```

Başka bir örnek olarak, herhangi bir sayısal argümanı iki katına çıkaran, ancak ifadeleri olduğu gibi bırakan bir fonksiyon burada:

```jldoctest
julia> function make_expr2(op, opr1, opr2)
           opr1f, opr2f = map(x -> isa(x, Number) ? 2*x : x, (opr1, opr2))
           retexpr = Expr(:call, op, opr1f, opr2f)
           return retexpr
       end
make_expr2 (generic function with 1 method)

julia> make_expr2(:+, 1, 2)
:(2 + 4)

julia> ex = make_expr2(:+, 1, Expr(:call, :*, 5, 8))
:(2 + 5 * 8)

julia> eval(ex)
42
```

## [Macros](@id man-macros)

Makrolar, bir programın nihai gövdesine üretilen kodu dahil etme mekanizması sağlar. Bir makro, bir argüman demetini döndürülen *ifade* ile eşler ve sonuçta elde edilen ifade, bir çalışma zamanı [`eval`](@ref) çağrısına ihtiyaç duymadan doğrudan derlenir. Makro argümanları ifadeleri, sabit değerleri ve sembolleri içerebilir.

### Basics

İşte son derece basit bir makro:

```jldoctest sayhello
julia> macro sayhello()
           return :( println("Hello, world!") )
       end
@sayhello (macro with 1 method)
```

Makroların Julia'nın sözdiziminde özel bir karakteri vardır: `@` (at işareti), ardından `macro NAME ... end` bloğunda tanımlanan benzersiz ad gelir. Bu örnekte, derleyici `@sayhello` ifadesinin tüm örneklerini şunlarla değiştirecektir:

```julia
:( println("Hello, world!") )
```

`@sayhello` REPL'ye girildiğinde, ifade hemen yürütülür, bu nedenle yalnızca değerlendirme sonucunu görürüz:

```jldoctest sayhello
julia> @sayhello()
Hello, world!
```

Şimdi, biraz daha karmaşık bir makro düşünün:

```jldoctest sayhello2
julia> macro sayhello(name)
           return :( println("Hello, ", $name) )
       end
@sayhello (macro with 1 method)
```

Bu makro bir argüman alır: `name`. `@sayhello` ile karşılaşıldığında, alıntılanmış ifade, argümanın değerini nihai ifadeye yerleştirmek için *genişletilir*:

```jldoctest sayhello2
julia> @sayhello("human")
Hello, human
```

Alıntılanan dönüş ifadesini [`macroexpand`](@ref) fonksiyonunu kullanarak görüntüleyebiliriz (**önemli not:** bu, makroları hata ayıklamak için son derece yararlı bir araçtır):

```julia-repl sayhello2
julia> ex = macroexpand(Main, :(@sayhello("human")) )
:(Main.println("Hello, ", "human"))

julia> typeof(ex)
Expr
```

Görüyoruz ki `"human"` literali ifadeye yerleştirilmiş.

Ayrıca, belki de `macroexpand` fonksiyonundan biraz daha kullanışlı olan [`@macroexpand`](@ref) adlı bir makro da vardır:

```jldoctest sayhello2
julia> @macroexpand @sayhello "human"
:(println("Hello, ", "human"))
```

### Hold up: why macros?

Zaten önceki bir bölümde `f(::Expr...) -> Expr` şeklinde bir fonksiyon gördük. Aslında, [`macroexpand`](@ref) da böyle bir fonksiyondur. Peki, makrolar neden var?

Makrolar gereklidir çünkü kod ayrıştırıldığında çalıştırılırlar, bu nedenle makrolar programcının tam program çalıştırılmadan *önce* özelleştirilmiş kod parçalarını oluşturmasına ve dahil etmesine olanak tanır. Farkı göstermek için, aşağıdaki örneği düşünün:

```julia-repl whymacros
julia> macro twostep(arg)
           println("I execute at parse time. The argument is: ", arg)
           return :(println("I execute at runtime. The argument is: ", $arg))
       end
@twostep (macro with 1 method)

julia> ex = macroexpand(Main, :(@twostep :(1, 2, 3)) );
I execute at parse time. The argument is: :((1, 2, 3))
```

İlk [`println`](@ref) çağrısı, [`macroexpand`](@ref) çağrıldığında yürütülür. Elde edilen ifade *yalnızca* ikinci `println`'i içerir:

```julia-repl whymacros
julia> typeof(ex)
Expr

julia> ex
:(println("I execute at runtime. The argument is: ", $(Expr(:copyast, :($(QuoteNode(:((1, 2, 3)))))))))

julia> eval(ex)
I execute at runtime. The argument is: (1, 2, 3)
```

### Macro invocation

Makrolar aşağıdaki genel sözdizimi ile çağrılır:

```julia
@name expr1 expr2 ...
@name(expr1, expr2, ...)
```

Makro adının önündeki ayırt edici `@` işaretine ve ilk formda argüman ifadeleri arasında virgül olmamasına, ayrıca ikinci formda `@name` sonrasında boşluk olmamasına dikkat edin. İki stil karıştırılmamalıdır. Örneğin, aşağıdaki sözdizimi yukarıdaki örneklerden farklıdır; `(expr1, expr2, ...)` demetini makroya bir argüman olarak geçirir:

```julia
@name (expr1, expr2, ...)
```

Bir dizi literalı (veya anlama) üzerinde bir makroyu çağırmanın alternatif bir yolu, parantez kullanmadan her ikisini yan yana koymaktır. Bu durumda, dizi makroya beslenen tek ifade olacaktır. Aşağıdaki sözdizimi eşdeğerdir (ve `@name [a b] * v`'den farklıdır):

```julia
@name[a b] * v
@name([a b]) * v
```

Makroların argümanlarını ifadeler, sabitler veya semboller olarak aldığını vurgulamak önemlidir. Makro argümanlarını keşfetmenin bir yolu, makro gövdesi içinde [`show`](@ref) fonksiyonunu çağırmaktır:

```jldoctest
julia> macro showarg(x)
           show(x)
           # ... remainder of macro, returning an expression
       end
@showarg (macro with 1 method)

julia> @showarg(a)
:a

julia> @showarg(1+1)
:(1 + 1)

julia> @showarg(println("Yo!"))
:(println("Yo!"))

julia> @showarg(1)        # Numeric literal
1

julia> @showarg("Yo!")    # String literal
"Yo!"

julia> @showarg("Yo! $("hello")")    # String with interpolation is an Expr rather than a String
:("Yo! $("hello")")
```

Verilen argüman listesine ek olarak, her makroya `__source__` ve `__module__` adında ekstra argümanlar geçilir.

`__source__` argümanı, makro çağrısındaki `@` işaretinin ayrıştırıcı konumu hakkında bilgi sağlayan bir `LineNumberNode` nesnesidir. Bu, makroların daha iyi hata tanılama bilgileri içermesine olanak tanır ve genellikle günlükleme, dize ayrıştırıcı makroları ve belgeler gibi alanlarda kullanılır; örneğin, [`@__LINE__`](@ref), [`@__FILE__`](@ref) ve [`@__DIR__`](@ref) makrolarını uygulamak için de kullanılır.

Konum bilgilerine `__source__.line` ve `__source__.file` referanslarıyla erişilebilir:

```jldoctest
julia> macro __LOCATION__(); return QuoteNode(__source__); end
@__LOCATION__ (macro with 1 method)

julia> dump(
            @__LOCATION__(
       ))
LineNumberNode
  line: Int64 2
  file: Symbol none
```

`__module__` argümanı, makro çağrısının genişletme bağlamı hakkında bilgi (bir `Module` nesnesi biçiminde) sağlar. Bu, makroların mevcut bağlam bilgilerini, örneğin mevcut bağlamları aramasına veya değeri mevcut modülde kendine yansıma yapan bir çalışma zamanı işlev çağrısına ek bir argüman olarak eklemesine olanak tanır.

### Building an advanced macro

İşte Julia'nın [`@assert`](@ref) makrosunun basitleştirilmiş bir tanımı:

```jldoctest building
julia> macro assert(ex)
           return :( $ex ? nothing : throw(AssertionError($(string(ex)))) )
       end
@assert (macro with 1 method)
```

Bu makro şu şekilde kullanılabilir:

```jldoctest building
julia> @assert 1 == 1.0

julia> @assert 1 == 0
ERROR: AssertionError: 1 == 0
```

Yazılı sözdiziminin yerinde, makro çağrısı ayrıştırma zamanında döndürülen sonucu genişletir. Bu, şunları yazmakla eşdeğerdir:

```julia
1 == 1.0 ? nothing : throw(AssertionError("1 == 1.0"))
1 == 0 ? nothing : throw(AssertionError("1 == 0"))
```

Yani, ilk çağrıda, `:(1 == 1.0)` ifadesi test koşulu slotuna eklenirken, `string(:(1 == 1.0))` değerinin de doğrulama mesajı slotuna eklendiği yer. Böylece, bu şekilde oluşturulan tüm ifade, `@assert` makro çağrısının gerçekleştiği sözdizim ağacına yerleştirilir. Daha sonra yürütme zamanında, eğer test ifadesi doğru olarak değerlendirilirse, [`nothing`](@ref) döndürülür, eğer test yanlışsa, yanlış olan doğrulanan ifadeyi belirten bir hata oluşur. Bu durumun bir fonksiyon olarak yazılmasının mümkün olmadığını unutmayın, çünkü yalnızca koşulun *değeri* mevcut ve hata mesajında onu hesaplayan ifadeyi göstermek imkansız olacaktır.

`@assert`'in gerçek tanımı Julia Base'te daha karmaşıktır. Kullanıcının yalnızca başarısız ifadeyi yazdırmak yerine kendi hata mesajını isteğe bağlı olarak belirtmesine izin verir. Değişken sayıda argümanla işlevlerde olduğu gibi ([Varargs Functions](@ref)), bu son argümandan sonra bir üç nokta ile belirtilir:

```jldoctest assert2
julia> macro assert(ex, msgs...)
           msg_body = isempty(msgs) ? ex : msgs[1]
           msg = string(msg_body)
           return :($ex ? nothing : throw(AssertionError($msg)))
       end
@assert (macro with 1 method)
```

Şimdi `@assert` iki çalışma moduna sahiptir, aldığı argüman sayısına bağlı olarak! Eğer yalnızca bir argüman varsa, `msgs` tarafından yakalanan ifadeler tuple'ı boş olacak ve yukarıdaki daha basit tanım ile aynı şekilde davranacaktır. Ancak şimdi kullanıcı ikinci bir argüman belirttiğinde, bu, başarısız olan ifadenin yerine mesaj gövdesinde yazdırılır. Bir makro genişletmesinin sonucunu, uygun şekilde adlandırılmış [`@macroexpand`](@ref) makrosu ile inceleyebilirsiniz:

```julia-repl assert2
julia> @macroexpand @assert a == b
:(if Main.a == Main.b
        Main.nothing
    else
        Main.throw(Main.AssertionError("a == b"))
    end)

julia> @macroexpand @assert a==b "a should equal b!"
:(if Main.a == Main.b
        Main.nothing
    else
        Main.throw(Main.AssertionError("a should equal b!"))
    end)
```

Başka bir durum daha var ki, gerçek `@assert` makrosu bunu ele alıyor: "a b'ye eşit olmalı" ifadesinin yanı sıra, değerlerini de yazdırmak istesek ne olur? Kişi, özel mesajda dize interpolasyonu kullanmayı naifçe deneyebilir, örneğin `@assert a==b "a ($a) b ($b) ile eşit olmalı!"`, ancak bu yukarıdaki makro ile beklenildiği gibi çalışmayacaktır. Nedenini görebiliyor musun? [string interpolation](@ref string-interpolation)'dan hatırlarsan, bir interpolasyonlu dize [`string`](@ref) çağrısına yeniden yazılır. Karşılaştır:

```jldoctest
julia> typeof(:("a should equal b"))
String

julia> typeof(:("a ($a) should equal b ($b)!"))
Expr

julia> dump(:("a ($a) should equal b ($b)!"))
Expr
  head: Symbol string
  args: Array{Any}((5,))
    1: String "a ("
    2: Symbol a
    3: String ") should equal b ("
    4: Symbol b
    5: String ")!"
```

Artık `msg_body` içinde düz bir dize almak yerine, beklenildiği gibi görüntülenmesi için değerlendirilmesi gereken tam bir ifade alınıyor. Bu, [`string`](@ref) çağrısına bir argüman olarak döndürülen ifadeye doğrudan eklenebilir; tam uygulama için [`error.jl`](https://github.com/JuliaLang/julia/blob/master/base/error.jl)'ye bakın.

`@assert` makrosu, makro gövdesindeki ifadelerin manipülasyonunu basitleştirmek için alıntılanmış ifadelere ekleme yapma işlevini büyük ölçüde kullanır.

### Hygiene

Daha karmaşık makrolarda ortaya çıkan bir sorun, [hygiene](https://en.wikipedia.org/wiki/Hygienic_macro) konusudur. Kısacası, makrolar, döndürülen ifadelerinde tanıttıkları değişkenlerin, genişledikleri çevredeki mevcut değişkenlerle yanlışlıkla çakışmadığından emin olmalıdır. Tersine, bir makroya argüman olarak geçirilen ifadelerin genellikle çevredeki kodun bağlamında değerlendirilmesi *beklenir*, mevcut değişkenlerle etkileşimde bulunarak ve onları değiştirerek. Başka bir endişe, bir makronun tanımlandığı modülden farklı bir modülde çağrılabilmesidir. Bu durumda, tüm küresel değişkenlerin doğru modüle çözülmesini sağlamak gerekir. Julia, yalnızca döndürülen ifadeyi dikkate alması gerektiği için (C gibi metin tabanlı makro genişletme dillerine göre) büyük bir avantaja sahiptir. Diğer tüm değişkenler (yukarıdaki `@assert` içindeki `msg` gibi) [normal scoping block behavior](@ref scope-of-variables) kuralını takip eder.

Bu sorunları göstermek için, bir ifade argümanı olarak alan `@time` makrosunu yazmayı düşünelim. Bu makro, zamanı kaydeder, ifadeyi değerlendirir, tekrar zamanı kaydeder, önceki ve sonraki zamanlar arasındaki farkı yazdırır ve ardından ifadenin değerini son değer olarak alır. Makro şu şekilde görünebilir:

```julia
macro time(ex)
    return quote
        local t0 = time_ns()
        local val = $ex
        local t1 = time_ns()
        println("elapsed time: ", (t1-t0)/1e9, " seconds")
        val
    end
end
```

Burada, `t0`, `t1` ve `val`'in özel geçici değişkenler olmasını istiyoruz ve `time_ns`'in Julia Base'deki [`time_ns`](@ref) fonksiyonuna atıfta bulunmasını istiyoruz, kullanıcının sahip olabileceği herhangi bir `time_ns` değişkenine değil (aynı şey `println` için de geçerlidir). Kullanıcı ifadesi `ex`'in de `t0` adında bir değişkene atama yaptığı veya kendi `time_ns` değişkenini tanımladığı durumlarda ortaya çıkabilecek sorunları hayal edin. Hatalar alabiliriz veya gizemli bir şekilde yanlış davranışlar görebiliriz.

Julia'nın makro genişletici bu sorunları şu şekilde çözer. Öncelikle, bir makro sonucundaki değişkenler yerel veya küresel olarak sınıflandırılır. Bir değişken, atandığında (ve küresel olarak ilan edilmediğinde), yerel olarak ilan edildiğinde veya bir fonksiyon argümanı adı olarak kullanıldığında yerel olarak kabul edilir. Aksi takdirde, küresel olarak kabul edilir. Yerel değişkenler daha sonra benzersiz olacak şekilde yeniden adlandırılır (yeni semboller üreten [`gensym`](@ref) fonksiyonu kullanılarak) ve küresel değişkenler makro tanım ortamında çözülür. Bu nedenle, yukarıdaki her iki endişe de ele alınır; makronun yerel değişkenleri kullanıcı değişkenleriyle çakışmayacak ve `time_ns` ile `println` Julia Temel tanımlarına atıfta bulunacaktır.

Bir sorun daha var. Ancak, bu makronun aşağıdaki kullanımını düşünün:

```julia
module MyModule
import Base.@time

time_ns() = ... # compute something

@time time_ns()
end
```

Burada kullanıcı ifadesi `ex`, makronun kullandığı `time_ns` fonksiyonu ile aynı olmayan bir `time_ns` çağrısıdır. Açıkça `MyModule.time_ns`'ye atıfta bulunmaktadır. Bu nedenle, `ex` içindeki kodun makro çağrısı ortamında çözülmesini sağlamalıyız. Bu, ifadeyi [`esc`](@ref) ile "kaçırarak" yapılır:

```julia
macro time(ex)
    ...
    local val = $(esc(ex))
    ...
end
```

Bu şekilde sarılmış bir ifade, makro genişletici tarafından olduğu gibi bırakılır ve çıktıya kelimesi kelimesine yapıştırılır. Bu nedenle, makro çağrısı ortamında çözülecektir.

Bu kaçış mekanizması, gerektiğinde kullanıcı değişkenlerini tanıtmak veya manipüle etmek için hijyeni "ihlal" etmek amacıyla kullanılabilir. Örneğin, aşağıdaki makro `x`'i çağrı ortamında sıfıra ayarlar:

```jldoctest
julia> macro zerox()
           return esc(:(x = 0))
       end
@zerox (macro with 1 method)

julia> function foo()
           x = 1
           @zerox
           return x # is zero
       end
foo (generic function with 1 method)

julia> foo()
0
```

Bu tür değişken manipülasyonu dikkatli bir şekilde kullanılmalıdır, ancak zaman zaman oldukça kullanışlıdır.

Hijyen kurallarını doğru bir şekilde uygulamak zor bir meydan okuma olabilir. Bir makro kullanmadan önce, bir fonksiyon kapanışının yeterli olup olmadığını düşünmek isteyebilirsiniz. Diğer bir faydalı strateji, mümkün olduğunca fazla işi çalışma zamanına ertelemektir. Örneğin, birçok makro argümanlarını basitçe bir `QuoteNode` veya diğer benzer [`Expr`](@ref) içine sarar. Bunun bazı örnekleri, basitçe `schedule(Task(() -> $body))` döndüren `@task body` ve basitçe `eval(QuoteNode(expr))` döndüren `@eval expr`'dir.

Açıklamak için, yukarıdaki `@time` örneğini şu şekilde yeniden yazabiliriz:

```julia
macro time(expr)
    return :(timeit(() -> $(esc(expr))))
end
function timeit(f)
    t0 = time_ns()
    val = f()
    t1 = time_ns()
    println("elapsed time: ", (t1-t0)/1e9, " seconds")
    return val
end
```

Ancak, bunu iyi bir sebepten dolayı yapmıyoruz: `expr`'i yeni bir kapsam bloğuna (anonim fonksiyon) sarmak, ifadenin anlamını (içindeki herhangi bir değişkenin kapsamını) biraz değiştirir; oysa `@time`'ın sarılı kod üzerinde minimum etki ile kullanılabilir olmasını istiyoruz.

### Macros and dispatch

Makrolar, Julia fonksiyonları gibi, genel niteliktedir. Bu, çoklu dispatch sayesinde birden fazla yöntem tanımına sahip olabilecekleri anlamına gelir:

```jldoctest macromethods
julia> macro m end
@m (macro with 0 methods)

julia> macro m(args...)
           println("$(length(args)) arguments")
       end
@m (macro with 1 method)

julia> macro m(x,y)
           println("Two arguments")
       end
@m (macro with 2 methods)

julia> @m "asd"
1 arguments

julia> @m 1 2
Two arguments
```

Ancak, makro yönlendirmesinin, makroya verilen AST türlerine dayandığını, AST'nin çalışma zamanında değerlendiği türlere değil, unutmamak gerekir:

```jldoctest macromethods
julia> macro m(::Int)
           println("An Integer")
       end
@m (macro with 3 methods)

julia> @m 2
An Integer

julia> x = 2
2

julia> @m x
1 arguments
```

## Code Generation

Önemli miktarda tekrarlayan şablon kodu gerektiğinde, tekrarları önlemek için genellikle bunu programatik olarak oluşturmak yaygındır. Çoğu dilde, bu ekstra bir derleme adımı ve tekrarlayan kodu oluşturmak için ayrı bir program gerektirir. Julia'da, ifade interpolasyonu ve [`eval`](@ref) bu tür kod üretiminin program yürütme sürecinde gerçekleşmesine olanak tanır. Örneğin, aşağıdaki özel türü düşünün.

```jldoctest mynumber-codegen
struct MyNumber
    x::Float64
end
# output

```

eklemek istediğimiz bir dizi yöntem için. Bunu aşağıdaki döngüde programatik olarak yapabiliriz:

```jldoctest mynumber-codegen
for op = (:sin, :cos, :tan, :log, :exp)
    eval(quote
        Base.$op(a::MyNumber) = MyNumber($op(a.x))
    end)
end
# output

```

ve şimdi bu işlevleri özel türümüzle kullanabiliriz:

```jldoctest mynumber-codegen
julia> x = MyNumber(π)
MyNumber(3.141592653589793)

julia> sin(x)
MyNumber(1.2246467991473532e-16)

julia> cos(x)
MyNumber(-1.0)
```

Bu şekilde, Julia kendi [preprocessor](https://en.wikipedia.org/wiki/Preprocessor) olarak hareket eder ve dilin içinden kod üretimine olanak tanır. Yukarıdaki kod, `:` ön ek alıntı biçimini kullanarak biraz daha özlü bir şekilde yazılabilir:

```julia
for op = (:sin, :cos, :tan, :log, :exp)
    eval(:(Base.$op(a::MyNumber) = MyNumber($op(a.x))))
end
```

Bu tür bir dil içi kod üretimi, `eval(quote(...))` desenini kullanarak, o kadar yaygındır ki Julia, bu deseni kısaltmak için bir makro ile birlikte gelir:

```julia
for op = (:sin, :cos, :tan, :log, :exp)
    @eval Base.$op(a::MyNumber) = MyNumber($op(a.x))
end
```

[`@eval`](@ref) makrosu, bu çağrıyı yukarıdaki daha uzun versiyonlarla tam olarak eşdeğer olacak şekilde yeniden yazar. Üretilen kodun daha uzun blokları için, `4d61726b646f776e2e436f64652822222c2022406576616c2229_40726566`'ya verilen ifade argümanı bir blok olabilir:

```julia
@eval begin
    # multiple lines
end
```

## [Non-Standard String Literals](@id meta-non-standard-string-literals)

[Strings](@ref non-standard-string-literals)'ten hatırlayın ki, bir tanımlayıcı ile ön eklenmiş dize literalleri standart dışı dize literalleri olarak adlandırılır ve ön eklenmemiş dize literallerinden farklı anlamlara sahip olabilirler. Örneğin:

  * `r"^\s*(?:#|$)"` [regular expression object](@ref man-regex-literals) değil bir dize üretir.
  * `b"DATA\xff\u2200"` bir [byte array literal](@ref man-byte-array-literals) için `[68,65,84,65,255,226,136,128]`.

Belki de şaşırtıcı, bu davranışlar Julia ayrıştırıcısına veya derleyicisine sabit kodlanmamıştır. Bunun yerine, herkesin kullanabileceği genel bir mekanizma tarafından sağlanan özel davranışlardır: ön ekli dize literalleri, özel adlandırılmış makrolara yapılan çağrılar olarak ayrıştırılır. Örneğin, düzenli ifade makrosu sadece şudur:

```julia
macro r_str(p)
    Regex(p)
end
```

Bu kadar. Bu makro, `r"^\s*(?:#|$)"` dize literalinin içeriklerinin `@r_str` makrosuna iletilmesi gerektiğini ve bu genişletmenin sonucunun dize literalinin bulunduğu yerin sözdizim ağaçsında yer alması gerektiğini belirtir. Diğer bir deyişle, `r"^\s*(?:#|$)"` ifadesi, aşağıdaki nesneyi doğrudan sözdizim ağaçsına yerleştirmekle eşdeğerdir:

```julia
Regex("^\\s*(?:#|\$)")
```

Dizek, dizek literal biçimi daha kısa ve çok daha kullanışlı olmakla kalmaz, aynı zamanda daha da verimlidir: çünkü düzenli ifade derlenir ve `Regex` nesnesi aslında *kod derlendiğinde* oluşturulur, derleme yalnızca bir kez gerçekleşir, kod her çalıştırıldığında değil. Düzenli ifadenin bir döngüde geçtiğini düşünün:

```julia
for line = lines
    m = match(r"^\s*(?:#|$)", line)
    if m === nothing
        # non-comment
    else
        # comment
    end
end
```

Düzenli ifade `r"^\s*(?:#|$)"` derlendiği ve bu kod ayrıştırıldığında sözdizim ağacına eklendiği için, ifade yalnızca bir kez derlenir, döngü her çalıştığında değil. Bunu makrolar olmadan başarmak için, bu döngüyü şu şekilde yazmak gerekir:

```julia
re = Regex("^\\s*(?:#|\$)")
for line = lines
    m = match(re, line)
    if m === nothing
        # non-comment
    else
        # comment
    end
end
```

Ayrıca, derleyici regex nesnesinin tüm döngüler boyunca sabit olduğunu belirleyemezse, belirli optimizasyonlar mümkün olmayabilir ve bu versiyon, yukarıdaki daha kullanışlı literal formdan hala daha az verimli hale gelebilir. Elbette, literal formun daha kullanışlı olduğu durumlar da vardır: bir değişkeni düzenli ifadeye yerleştirmek gerekiyorsa, bu daha ayrıntılı yaklaşımı benimsemek zorundasınız; düzenli ifade deseninin kendisi dinamikse ve her döngü yinelemesinde potansiyel olarak değişiyorsa, her yinelemede yeni bir düzenli ifade nesnesi oluşturulmalıdır. Ancak, kullanım durumlarının büyük çoğunluğunda, düzenli ifadeler çalışma zamanı verilerine dayalı olarak oluşturulmaz. Bu çoğunluk durumunda, düzenli ifadeleri derleme zamanı değerleri olarak yazma yeteneği paha biçilmezdir.

Kullanıcı tanımlı dize literalleri için mekanizma derin, son derece güçlüdür. Sadece Julia'nın standart dışı literalleri bununla uygulanmakla kalmaz, aynı zamanda komut literal sözdizimi (``` `echo "Hello, $person"` ```) de aşağıdaki masum görünümlü makro kullanılarak uygulanır:

```julia
macro cmd(str)
    :(cmd_gen($(shell_parse(str)[1])))
end
```

Elbette, bu makro tanımında kullanılan fonksiyonlarda büyük bir karmaşıklık gizlidir, ancak bunlar sadece fonksiyonlardır, tamamen Julia'da yazılmıştır. Kaynak kodlarını okuyabilir ve tam olarak ne yaptıklarını görebilirsiniz - ve yaptıkları tek şey, programınızın sözdizim ağaçlarına yerleştirilecek ifade nesneleri oluşturmaktır.

Dize string literal'ları gibi, komut literal'ları da özel adlarla ön eklenerek "standart dışı komut literal'ları" oluşturabilir. Bu komut literal'ları, özel adlandırılmış makrolara yapılan çağrılar olarak ayrıştırılır. Örneğin, sözdizimi ```custom`literal` ``` `@custom_cmd "literal"` olarak ayrıştırılır. Julia'nın kendisi herhangi bir standart dışı komut literal'ı içermez, ancak paketler bu sözdizimini kullanabilir. Farklı sözdizimi ve `_str` son eki yerine `_cmd` son eki dışında, standart dışı komut literal'ları tam olarak standart dışı string literal'ları gibi davranır.

İki modül aynı isimde standart dışı dize veya komut literalleri sağladığında, dize veya komut literalini bir modül adıyla nitelendirmek mümkündür. Örneğin, hem `Foo` hem de `Bar` standart dışı dize literali `@x_str` sağlıyorsa, aralarındaki ayrımı yapmak için `Foo.x"literal"` veya `Bar.x"literal"` yazılabilir.

Bir makroyu tanımlamanın başka bir yolu şöyle olabilir:

```julia
macro foo_str(str, flag)
    # do stuff
end
```

Bu makro, aşağıdaki sözdizimi ile çağrılabilir:

```julia
foo"str"flag
```

Yukarıda belirtilen sözdizimindeki bayrak türü, string literalinin ardından gelen içeriklerle bir `String` olacaktır.

## Generated functions

Çok özel bir makro [`@generated`](@ref)'dır; bu, *üretken fonksiyonlar* olarak adlandırılanları tanımlamanıza olanak tanır. Bu fonksiyonlar, argümanlarının türlerine bağlı olarak daha fazla esneklik ve/veya daha az kod ile özel kod üretebilme yeteneğine sahiptir; bu, çoklu dağıtım ile elde edilebileceklerden daha fazlasıdır. Makrolar, ayrıştırma zamanında ifadelerle çalışır ve girdilerinin türlerine erişemezken, bir üretken fonksiyon, argümanların türlerinin bilindiği bir zamanda genişletilir, ancak fonksiyon henüz derlenmemiştir.

Belli bir hesaplama veya eylem gerçekleştirmek yerine, üretilen bir fonksiyon bildirimi, argümanların türlerine karşılık gelen yöntemin gövdesini oluşturan alıntılanmış bir ifade döndürür. Üretilen bir fonksiyon çağrıldığında, döndürdüğü ifade derlenir ve ardından çalıştırılır. Bunu verimli hale getirmek için, sonuç genellikle önbelleğe alınır. Ve bunu çıkarılabilir hale getirmek için, yalnızca dilin sınırlı bir alt kümesi kullanılabilir. Böylece, üretilen fonksiyonlar, izin verilen yapılar üzerinde daha büyük kısıtlamalar pahasına, işi çalışma zamanından derleme zamanına taşımak için esnek bir yol sağlar.

Üretilen fonksiyonları tanımlarken, sıradan fonksiyonlara göre beş ana fark vardır:

1. Fonksiyon bildirimini `@generated` makrosu ile not edersiniz. Bu, derleyiciye bu fonksiyonun üretilmiş bir fonksiyon olduğunu bildiren AST'ye bazı bilgiler ekler.
2. Üretilen fonksiyonun gövdesinde yalnızca argümanların *türlerine* erişiminiz vardır – değerlerine değil.
3. Bunun yerine bir şey hesaplamak veya bir eylem gerçekleştirmek yerine, istediğin şeyi yapan bir *alıntı ifadesi* döndürüyorsun.
4. Üretilen fonksiyonlar yalnızca üretilen fonksiyonun tanımından *önce* tanımlanmış olan fonksiyonları çağırabilir. (Bunu takip etmemek, gelecekteki bir dünya çağındaki fonksiyonlara atıfta bulunan `MethodErrors` ile sonuçlanabilir.)
5. Üretilen fonksiyonlar, herhangi bir sabit olmayan küresel durumu (örneğin, IO, kilitler, yerel olmayan sözlükler veya [`hasmethod`](@ref) kullanmak gibi) *değiştirmemeli* veya *gözlemlememelidir*. Bu, yalnızca küresel sabitleri okuyabilecekleri ve yan etkileri olamayacağı anlamına gelir. Diğer bir deyişle, tamamen saf olmalıdırlar. Bir uygulama sınırlaması nedeniyle, şu anda bir kapanış veya jeneratör tanımlayamazlar.

En iyi örnekle açıklamak mümkündür. Üretilen bir fonksiyonu `foo` olarak tanımlayabiliriz.

```jldoctest generated
julia> @generated function foo(x)
           Core.println(x)
           return :(x * x)
       end
foo (generic function with 1 method)
```

Not edin ki, gövde bir alıntı ifadesi döner, yani `:(x * x)`, sadece `x * x` değerini değil.

Arayanın bakış açısından, bu, normal bir işlevle aynı; aslında, bir normal veya üretilmiş işlev çağırdığınızı bilmenize gerek yok. `foo`'nun nasıl davrandığına bir bakalım:

```jldoctest generated
julia> x = foo(2); # note: output is from println() statement in the body
Int64

julia> x           # now we print x
4

julia> y = foo("bar");
String

julia> y
"barbar"
```

Yani, oluşturulan fonksiyonun gövdesinde, `x` geçirilen argümanın *tipi*dir ve oluşturulan fonksiyonun döndürdüğü değer, tanımdan döndürdüğümüz alıntılanmış ifadenin, şimdi `x`'in *değeri* ile değerlendirilmesinin sonucudur.

Eğer daha önce kullandığımız bir tür ile `foo`'yu tekrar değerlendirirsek, bu durum türün yeniden kullanılması anlamına gelir. Bu, genellikle tür sisteminin kurallarına bağlı olarak, türün daha önceki değerlendirmeleriyle çelişmemesi koşuluyla geçerli olabilir. Eğer tür uyumluysa, işlem sorunsuz bir şekilde devam eder. Ancak, tür çelişkileri veya uyumsuzlukları varsa, bu durum hata ile sonuçlanabilir.

```jldoctest generated
julia> foo(4)
16
```

Not edin ki [`Int64`](@ref) için bir çıktı yok. Oluşturulan fonksiyonun gövdesinin burada yalnızca bir kez, belirli bir argüman türü seti için çalıştırıldığını görebiliriz ve sonuç önbelleğe alındı. Daha sonra, bu örnek için, ilk çağrıda oluşturulan fonksiyondan dönen ifade, yöntem gövdesi olarak yeniden kullanıldı. Ancak, gerçek önbellekleme davranışı, uygulama tanımlı bir performans optimizasyonudur, bu nedenle bu davranışa çok fazla bağımlı olmak geçersizdir.

Üretilen bir fonksiyonun üretilme sayısı *bir kez* olabilir, ancak *daha sık* da olabilir ya da hiç gerçekleşmiyor gibi görünebilir. Sonuç olarak, yan etkileri olan bir üretilen fonksiyonu *asla* yazmamalısınız - yan etkilerin ne zaman ve ne sıklıkla gerçekleşeceği belirsizdir. (Bu, makrolar için de geçerlidir - ve makrolar için olduğu gibi, [`eval`](@ref)'nın bir üretilen fonksiyonda kullanılması, yanlış bir şey yaptığınızın bir işaretidir.) Ancak, makrolardan farklı olarak, çalışma zamanı sistemi `4d61726b646f776e2e436f64652822222c20226576616c2229_40726566` çağrısını doğru bir şekilde işleyemez, bu nedenle bu yasaktır.

`@generated` fonksiyonlarının yöntem yeniden tanımlamasıyla nasıl etkileşime girdiğini görmek de önemlidir. Doğru bir `@generated` fonksiyonunun herhangi bir değişken durumu gözlemlememesi veya küresel durumu değiştirmemesi gerektiği ilkesini takip ederek, aşağıdaki davranışı görüyoruz. Oluşturulan fonksiyonun, oluşturulan fonksiyonun kendisinin *tanımından* önce tanımlanmamış herhangi bir yöntemi *çağırması* mümkün değildir.

Başlangıçta `f(x)`'in bir tanımı vardı.

```jldoctest redefinition
julia> f(x) = "original definition";
```

Diğer `f(x)` kullanan işlemleri tanımlayın:

```jldoctest redefinition
julia> g(x) = f(x);

julia> @generated gen1(x) = f(x);

julia> @generated gen2(x) = :(f(x));
```

Artık `f(x)` için bazı yeni tanımlar ekliyoruz:

```jldoctest redefinition
julia> f(x::Int) = "definition for Int";

julia> f(x::Type{Int}) = "definition for Type{Int}";
```

ve ve sonuçların nasıl farklılık gösterdiğini karşılaştırın:

```jldoctest redefinition
julia> f(1)
"definition for Int"

julia> g(1)
"definition for Int"

julia> gen1(1)
"original definition"

julia> gen2(1)
"definition for Int"
```

Her bir üretilen fonksiyonun yöntemi, tanımlı fonksiyonların kendi bakış açısına sahiptir:

```jldoctest redefinition
julia> @generated gen1(x::Real) = f(x);

julia> gen1(1)
"definition for Type{Int}"
```

Üstteki örneklenen `foo` fonksiyonu, normal bir fonksiyon olan `foo(x) = x * x`'in yapamadığı bir şey yapmadı (ilk çağrıda türü yazdırmak ve daha yüksek bir yük getirmek dışında). Ancak, bir üretilmiş fonksiyonun gücü, kendisine geçirilen türlere bağlı olarak farklı alıntılanmış ifadeleri hesaplama yeteneğinde yatar:

```jldoctest
julia> @generated function bar(x)
           if x <: Integer
               return :(x ^ 2)
           else
               return :(x)
           end
       end
bar (generic function with 1 method)

julia> bar(4)
16

julia> bar("baz")
"baz"
```

(bununla birlikte, elbette bu yapay örnek çoklu dağıtım kullanılarak daha kolay bir şekilde uygulanabilir...)

Bu bunu kötüye kullanmak çalışma zamanı sistemini bozacak ve tanımsız davranışa neden olacaktır:

```jldoctest
julia> @generated function baz(x)
           if rand() < .9
               return :(x^2)
           else
               return :("boo!")
           end
       end
baz (generic function with 1 method)
```

Üretilen fonksiyonun gövdesi belirlenmemiş olduğundan, davranışı, *ve tüm sonraki kodların davranışı* tanımsızdır.

*Bu örnekleri kopyalamayın!*

Bu örneklerin, üretilen fonksiyonların hem tanımında hem de çağrı yerinde nasıl çalıştığını göstermek için yardımcı olmasını umuyorum; ancak, *bunları kopyalamayın*, aşağıdaki nedenlerden dolayı:

  * `foo` fonksiyonu yan etkileri vardır ( `Core.println` çağrısı) ve bu yan etkilerin ne zaman, ne sıklıkta veya kaç kez gerçekleşeceği tam olarak belirsizdir.
  * `bar` fonksiyonu, çoklu dispatch ile daha iyi çözülen bir problemi çözer - `bar(x) = x` ve `bar(x::Integer) = x ^ 2` tanımlamak aynı şeyi yapar, ancak bu hem daha basit hem de daha hızlıdır.
  * `baz` fonksiyonu patolojik.

Not edin ki, oluşturulan bir fonksiyonda denenmemesi gereken işlemler kümesi sınırsızdır ve çalışma zamanı sistemi şu anda yalnızca geçersiz işlemlerin bir alt kümesini tespit edebilir. Bildirim olmaksızın genellikle kötü tanımla açıkça bağlantılı olmayan ince yollarla çalışma zamanı sistemini basitçe bozacak birçok başka işlem vardır. Fonksiyon üreteci çıkarım sırasında çalıştığı için, o kodun tüm sınırlamalarına saygı göstermelidir.

Bazı yapılmaması gereken işlemler şunlardır:

1. Yerel işaretçilerin önbelleğe alınması.
2. `Core.Compiler` içeriği veya yöntemleriyle herhangi bir şekilde etkileşimde bulunmak.
3. Herhangi bir değişken durumu gözlemleme.

      * Üretilen fonksiyon üzerindeki çıkarım, kodunuzun bu durumu gözlemlemeye veya değiştirmeye çalıştığı sırada *herhangi* bir zamanda çalıştırılabilir.
4. Herhangi bir kilit alma: Çağırdığınız C kodu dahili olarak kilitler kullanabilir, (örneğin, çoğu uygulamanın dahili olarak kilitler gerektirmesi nedeniyle `malloc` çağırmak sorun değildir) ancak Julia kodu çalıştırırken herhangi birini tutmaya veya almaya çalışmayın.
5. Üretilen fonksiyonun gövdesinden sonra tanımlanan herhangi bir fonksiyonu çağırmak. Bu koşul, modülde herhangi bir fonksiyonun çağrılmasına izin vermek için kısmen yüklenen önceden derlenmiş modüller için gevşetilmiştir.

Tamam, şimdi üretilen fonksiyonların nasıl çalıştığını daha iyi anladığımıza göre, bunları daha gelişmiş (ve geçerli) işlevsellikler oluşturmak için kullanalım...

### An advanced example

Julia'nın temel kütüphanesi, n boyutlu bir diziye, n çoklu indeks kümesine dayalı olarak doğrusal bir indeks hesaplamak için dahili bir `sub2ind` fonksiyonuna sahiptir - diğer bir deyişle, `A[x,y,z,...]` yerine `A[i]` kullanarak bir diziye indekslemek için kullanılabilecek `i` indeksini hesaplamak için. Olası bir uygulama aşağıdaki gibidir:

```jldoctest sub2ind
julia> function sub2ind_loop(dims::NTuple{N}, I::Integer...) where N
           ind = I[N] - 1
           for i = N-1:-1:1
               ind = I[i]-1 + dims[i]*ind
           end
           return ind + 1
       end;

julia> sub2ind_loop((3, 5), 1, 2)
4
```

Aynı şey özyineleme kullanılarak yapılabilir:

```jldoctest
julia> sub2ind_rec(dims::Tuple{}) = 1;

julia> sub2ind_rec(dims::Tuple{}, i1::Integer, I::Integer...) =
           i1 == 1 ? sub2ind_rec(dims, I...) : throw(BoundsError());

julia> sub2ind_rec(dims::Tuple{Integer, Vararg{Integer}}, i1::Integer) = i1;

julia> sub2ind_rec(dims::Tuple{Integer, Vararg{Integer}}, i1::Integer, I::Integer...) =
           i1 + dims[1] * (sub2ind_rec(Base.tail(dims), I...) - 1);

julia> sub2ind_rec((3, 5), 1, 2)
4
```

Her iki uygulama, farklı olmalarına rağmen, esasen aynı şeyi yapar: dizinin boyutları üzerinde bir çalışma zamanı döngüsü, her boyuttaki kaydırmayı nihai indekse toplar.

Ancak, döngü için ihtiyaç duyduğumuz tüm bilgiler, argümanların tür bilgisine gömülüdür. Bu, derleyicinin yinelemeyi derleme zamanına taşımasına ve çalışma zamanı döngülerini tamamen ortadan kaldırmasına olanak tanır. Benzer bir etkiyi elde etmek için üretilen fonksiyonları kullanabiliriz; derleyici dilinde, döngüyü manuel olarak açmak için üretilen fonksiyonları kullanırız. Gövde neredeyse aynı hale gelir, ancak doğrusal indeksi hesaplamak yerine, indeksi hesaplayan bir *ifade* oluştururuz:

```jldoctest sub2ind_gen
julia> @generated function sub2ind_gen(dims::NTuple{N}, I::Integer...) where N
           ex = :(I[$N] - 1)
           for i = (N - 1):-1:1
               ex = :(I[$i] - 1 + dims[$i] * $ex)
           end
           return :($ex + 1)
       end;

julia> sub2ind_gen((3, 5), 1, 2)
4
```

**Bu kod ne üretecek?**

Bir kolay yol, gövdeyi başka bir (normal) işleve çıkarmaktır:

```jldoctest sub2ind_gen2
julia> function sub2ind_gen_impl(dims::Type{T}, I...) where T <: NTuple{N,Any} where N
           length(I) == N || return :(error("partial indexing is unsupported"))
           ex = :(I[$N] - 1)
           for i = (N - 1):-1:1
               ex = :(I[$i] - 1 + dims[$i] * $ex)
           end
           return :($ex + 1)
       end;

julia> @generated function sub2ind_gen(dims::NTuple{N}, I::Integer...) where N
           return sub2ind_gen_impl(dims, I...)
       end;

julia> sub2ind_gen((3, 5), 1, 2)
4
```

Artık `sub2ind_gen_impl`'i çalıştırabilir ve döndürdüğü ifadeyi inceleyebiliriz:

```jldoctest sub2ind_gen2
julia> sub2ind_gen_impl(Tuple{Int,Int}, Int, Int)
:(((I[1] - 1) + dims[1] * (I[2] - 1)) + 1)
```

Yani, burada kullanılacak yöntem gövdesi hiç döngü içermiyor - sadece iki demet üzerinde indeksleme, çarpma ve toplama/çıkarma işlemleri var. Tüm döngüleme derleme zamanında gerçekleştiriliyor ve yürütme sırasında tamamen döngüden kaçınıyoruz. Böylece, yalnızca *her tür için bir kez* döngü yapıyoruz, bu durumda `N` başına bir kez (fonksiyon birden fazla kez oluşturulduğu kenar durumları hariç - yukarıdaki feragatnameye bakın).

### Optionally-generated functions

Üretilen fonksiyonlar çalışma zamanında yüksek verimlilik sağlayabilir, ancak derleme zamanı maliyeti ile birlikte gelir: her somut argüman türü kombinasyonu için yeni bir fonksiyon gövdesi üretilmelidir. Genellikle, Julia, herhangi bir argüman için çalışacak "genel" versiyonları derleyebilir, ancak üretilen fonksiyonlarla bu imkansızdır. Bu, üretilen fonksiyonları yoğun bir şekilde kullanan programların statik olarak derlenmesinin imkansız olabileceği anlamına gelir.

Bu problemi çözmek için, dil, üretilmiş fonksiyonların normal, üretilmemiş alternatif uygulamalarını yazmak için sözdizimi sağlar. Yukarıdaki `sub2ind` örneğine uygulandığında, şöyle görünecektir:

```jldoctest sub2ind_gen_opt
julia> function sub2ind_gen_impl(dims::Type{T}, I...) where T <: NTuple{N,Any} where N
           ex = :(I[$N] - 1)
           for i = (N - 1):-1:1
               ex = :(I[$i] - 1 + dims[$i] * $ex)
           end
           return :($ex + 1)
       end;

julia> function sub2ind_gen_fallback(dims::NTuple{N}, I) where N
           ind = I[N] - 1
           for i = (N - 1):-1:1
               ind = I[i] - 1 + dims[i]*ind
           end
           return ind + 1
       end;

julia> function sub2ind_gen(dims::NTuple{N}, I::Integer...) where N
           length(I) == N || error("partial indexing is unsupported")
           if @generated
               return sub2ind_gen_impl(dims, I...)
           else
               return sub2ind_gen_fallback(dims, I)
           end
       end;

julia> sub2ind_gen((3, 5), 1, 2)
4
```

İçsel olarak, bu kod fonksiyonun iki uygulamasını oluşturur: `if @generated` bloğundaki ilk blokun kullanıldığı bir üretilmiş versiyon ve `else` bloğunun kullanıldığı normal bir versiyon. `if @generated` bloğunun `then` kısmının içinde, kod diğer üretilmiş fonksiyonlarla aynı anlamı taşır: argüman adları tiplere atıfta bulunur ve kod bir ifade döndürmelidir. Birden fazla `if @generated` bloğu olabilir; bu durumda üretilmiş uygulama tüm `then` bloklarını kullanırken, alternatif uygulama tüm `else` bloklarını kullanır.

Dikkat edin ki, fonksiyonun başına bir hata kontrolü ekledik. Bu kod her iki versiyon için de ortak olacak ve her iki versiyonda da çalışma zamanı kodudur (oluşturulan versiyondan bir ifade olarak alıntılanacak ve döndürülecektir). Bu, yerel değişkenlerin değerlerinin ve türlerinin kod oluşturma zamanında mevcut olmadığı anlamına gelir - kod oluşturma kodu yalnızca argümanların türlerini görebilir.

Bu tanım tarzında, kod üretim özelliği esasen isteğe bağlı bir optimizasyondur. Derleyici bunu uygun olduğunda kullanacaktır, ancak aksi takdirde normal uygulamayı kullanmayı seçebilir. Bu tarz tercih edilmektedir, çünkü derleyicinin daha fazla karar vermesine ve programları daha fazla şekilde derlemesine olanak tanır ve normal kod, kod üreten koddan daha okunabilir. Ancak, hangi uygulamanın kullanıldığı derleyici uygulama ayrıntılarına bağlıdır, bu nedenle iki uygulamanın aynı şekilde davranması esastır.
