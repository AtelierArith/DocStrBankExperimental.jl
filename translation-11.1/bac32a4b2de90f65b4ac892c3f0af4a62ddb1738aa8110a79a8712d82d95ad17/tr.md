# Frequently Asked Questions

## General

### Is Julia named after someone or something?

Hayır.

### Why don't you compile Matlab/Python/R/… code to Julia?

Birçok insan diğer dinamik dillerin sözdizimiyle tanıdık olduğundan ve bu dillerde zaten birçok kod yazıldığından, neden sadece bir Matlab veya Python ön yüzünü bir Julia arka ucuna entegre etmediğimizi (veya kodu Julia'ya "dönüştürmediğimizi") merak etmek doğaldır. Tüm Julia'nın performans avantajlarını elde etmek için programcıların yeni bir dil öğrenmesini gerektirmeden. Basit, değil mi?

The basic issue is that there is *nothing special about Julia's compiler*: we use a commonplace compiler (LLVM) with no “secret sauce” that other language developers don't know about.  Indeed, Julia's compiler is in many ways much simpler than those of other dynamic languages (e.g. PyPy or LuaJIT).   Julia's performance advantage derives almost entirely from its front-end: its language semantics allow a [well-written Julia program](@ref man-performance-tips) to *give more opportunities to the compiler* to generate efficient code and memory layouts.  If you tried to compile Matlab or Python code to Julia, our compiler would be limited by the semantics of Matlab or Python to producing code no better than that of existing compilers for those languages (and probably worse).  The key role of semantics is also why several existing Python compilers (like Numba and Pythran) only attempt to optimize a small subset of the language (e.g. operations on Numpy arrays and scalars), and for this subset they are already doing at least as well as we could for the same semantics.  The people working on those projects are incredibly smart and have accomplished amazing things, but retrofitting a compiler onto a language that was designed to be interpreted is a very difficult problem.

Julia'nın avantajı, iyi performansın yalnızca "yerleşik" türler ve işlemlerle sınırlı olmaması ve yüksek seviyeli tür-generic kod yazmanın, hızlı ve bellek verimli kalırken, keyfi kullanıcı tanımlı türler üzerinde çalışabilmesidir. Python gibi dillerdeki türler, benzer yetenekler için derleyiciye yeterli bilgi sağlamaz, bu nedenle bu dilleri bir Julia ön ucu olarak kullandığınızda sıkışıp kalırsınız.

Benzer nedenlerle, otomatik çeviri ile Julia'ya geçiş genellikle okunaksız, yavaş ve idiyomatik olmayan kodlar üretir; bu da başka bir dilden yerel bir Julia portu için iyi bir başlangıç noktası olmaz.

Diğer yandan, dil *eşzamanlılığı* son derece faydalıdır: Julia'dan (ve tersine) diğer dillerdeki mevcut yüksek kaliteli kodları kullanmak istiyoruz! Bunu sağlamanın en iyi yolu bir transpiler değil, daha çok kolay dil arası çağrı olanaklarıdır. Bu konuda çok çalıştık; C ve Fortran kütüphanelerini çağırmak için yerleşik `ccall` iç işlevinden, Julia'yı Python, Matlab, C++ ve daha fazlasıyla bağlayan [JuliaInterop](https://github.com/JuliaInterop) paketlerine kadar.

## [Public API](@id man-api)

### How does Julia define its public API?

Julia'nın kamuya açık [API](https://en.wikipedia.org/wiki/API) belgesi, `Base` ve standart kütüphanelerden kamuya açık sembollerin belgelerinde tanımlanan davranıştır. Fonksiyonlar, türler ve sabitler, kamuya açık değillerse kamu API'sinin bir parçası değildir, belgeleri veya belgelerde tanımlanmış olsalar bile. Ayrıca, yalnızca kamuya açık sembollerin belgelenmiş davranışı kamu API'sinin bir parçasıdır. Kamuya açık sembollerin belgelenmemiş davranışı içseldir.

Halka semboller, ya `public foo` ya da `export foo` ile işaretlenmiş olanlardır.

Başka bir deyişle:

  * Belgelendirilmiş kamu sembollerinin davranışı, kamu API'sinin bir parçasıdır.
  * Belirlenmemiş davranışlar, kamuya açık API'nin bir parçası değildir.
  * Özel sembollerin belgelenmiş davranışı, genel API'nin bir parçası değildir.
  * Özel sembollerin belgelenmemiş davranışı, genel API'nin bir parçası değildir.

Bir modülden kamuya açık sembollerin tam listesini `names(MyModule)` ile alabilirsiniz.

Paket yazarlarının, kamu API'lerini benzer şekilde tanımlamaları teşvik edilmektedir.

Julia'nın Kamu API'sindeki her şey [SemVer](https://semver.org/) ile kapsanmıştır ve bu nedenle Julia 2.0'dan önce kaldırılmayacak veya anlamlı kırıcı değişiklikler almayacaktır.

### There is a useful undocumented function/type/constant. Can I use it?

Updating Julia may break your code if you use non-public API.  If the code is self-contained, it may be a good idea to copy it into your project.  If you want to rely on a complex non-public API, especially when using it from a stable package, it is a good idea to open an [issue](https://github.com/JuliaLang/julia/issues) or [pull request](https://github.com/JuliaLang/julia/pulls) to start a discussion for turning it into a public API.  However, we do not discourage the attempt to create packages that expose stable public interfaces while relying on non-public implementation details of Julia and buffering the differences across different Julia versions.

### The documentation is not accurate enough. Can I rely on the existing behavior?

Lütfen mevcut davranışı bir kamu API'sine dönüştürmek için bir tartışma başlatmak üzere [issue](https://github.com/JuliaLang/julia/issues) veya [pull request](https://github.com/JuliaLang/julia/pulls) adresini açın.

## Sessions and the REPL

### How do I delete an object in memory?

Julia, MATLAB'ın `clear` fonksiyonunun bir analoğuna sahip değildir; bir isim bir Julia oturumunda (teknik olarak, `Main` modülünde) tanımlandığında, her zaman mevcuttur.

Eğer bellek kullanımı sizin için bir endişe ise, nesneleri daha az bellek tüketenlerle her zaman değiştirebilirsiniz. Örneğin, `A` artık ihtiyaç duymadığınız bir gigabayt boyutunda dizi ise, belleği `A = nothing` ile serbest bırakabilirsiniz. Bellek, çöp toplayıcının bir sonraki çalıştığında serbest bırakılacaktır; bunu [`GC.gc()`](@ref Base.GC.gc) ile zorlayabilirsiniz. Ayrıca, `A`'yı kullanmaya çalışmak muhtemelen bir hatayla sonuçlanacaktır, çünkü çoğu yöntem `Nothing` türü üzerinde tanımlanmamıştır.

### How can I modify the declaration of a type in my session?

Belki bir tür tanımladınız ve ardından yeni bir alan eklemeniz gerektiğini fark ettiniz. Bunu REPL'de denerseniz, şu hatayı alırsınız:

```
ERROR: invalid redefinition of constant MyType
```

Modül `Main` içindeki türler yeniden tanımlanamaz.

Yeni kod geliştirirken bu rahatsız edici olabilir, ancak mükemmel bir çözüm var. Modüller, yeniden tanımlanarak değiştirilebilir, bu nedenle tüm yeni kodunuzu bir modülün içine sararsanız, türleri ve sabitleri yeniden tanımlayabilirsiniz. Tür adlarını `Main` içine aktaramazsınız ve orada yeniden tanımlama bekleyemezsiniz, ancak kapsamı çözmek için modül adını kullanabilirsiniz. Başka bir deyişle, geliştirme sırasında şöyle bir iş akışı kullanabilirsiniz:

```julia
include("mynewcode.jl")              # this defines a module MyModule
obj1 = MyModule.ObjConstructor(a, b)
obj2 = MyModule.somefunction(obj1)
# Got an error. Change something in "mynewcode.jl"
include("mynewcode.jl")              # reload the module
obj1 = MyModule.ObjConstructor(a, b) # old objects are no longer valid, must reconstruct
obj2 = MyModule.somefunction(obj1)   # this time it worked!
obj3 = MyModule.someotherfunction(obj2, c)
...
```

## [Scripting](@id man-scripting)

### How do I check if the current file is being run as the main script?

Bir dosya `julia file.jl` kullanılarak ana betik olarak çalıştırıldığında, komut satırı argüman işleme gibi ek işlevselliği etkinleştirmek isteyebilirsiniz. Bir dosyanın bu şekilde çalıştırılıp çalıştırılmadığını belirlemenin bir yolu, `abspath(PROGRAM_FILE) == @__FILE__` ifadesinin `true` olup olmadığını kontrol etmektir.

Ancak, hem bir betik hem de içe aktarılabilir bir kütüphane olarak işlev gören dosyalar yazmamanız önerilir. Hem bir kütüphane hem de bir betik olarak mevcut olan işlevselliğe ihtiyaç duyulursa, bunu bir kütüphane olarak yazmak ve ardından işlevselliği ayrı bir betiğe aktarmak daha iyidir.

### [How do I catch CTRL-C in a script?](@id catch-ctrl-c)

Bir Julia betiğini `julia file.jl` kullanarak çalıştırmak, CTRL-C (SIGINT) ile sonlandırmaya çalıştığınızda [`InterruptException`](@ref) hatasını vermez. Bir Julia betiğini sonlandırmadan önce belirli bir kod çalıştırmak için, bu CTRL-C ile veya olmayabilir, [`atexit`](@ref) kullanın. Alternatif olarak, `julia -e 'include(popfirst!(ARGS))' file.jl` kullanarak bir betiği çalıştırabilir ve [`try`](@ref) bloğunda `InterruptException` yakalayabilirsiniz. Bu strateji ile [`PROGRAM_FILE`](@ref) ayarlanmayacaktır.

### How do I pass options to `julia` using `#!/usr/bin/env`?

`julia`'ya seçenekler geçmek için, `#!/usr/bin/env julia --startup-file=no` gibi bir shebang satırı kullanmak, birçok platformda (BSD, macOS, Linux) çalışmayacaktır; çünkü çekirdek, kabuğun aksine, argümanları boşluk karakterlerinde ayırmaz. Tek bir argüman dizesini boşluklarda ayıran `env -S` seçeneği, bir kabuk gibi, basit bir çözüm sunar:

```julia
#!/usr/bin/env -S julia --color=yes --startup-file=no
@show ARGS  # put any Julia code here
```

!!! note
    Seçenek `env -S`, FreeBSD 6.0'da (2005), macOS Sierra'da (2016) ve GNU/Linux coreutils 8.30'da (2018) ortaya çıktı.


### Why doesn't `run` support `*` or pipes for scripting external programs?

Julia'nın [`run`](@ref) fonksiyonu dış programları *doğrudan* başlatır, [operating-system shell](https://en.wikipedia.org/wiki/Shell_(computing)) gibi bir `system("...")` fonksiyonunu çağırmadan (Python, R veya C gibi diğer dillerde). Bu, `run`'ın `*` için joker karakter genişletmesi yapmadığı anlamına gelir (["globbing"](https://en.wikipedia.org/wiki/Glob_(programming))), ayrıca [shell pipelines](https://en.wikipedia.org/wiki/Pipeline_(Unix)) gibi `|` veya `>` yorumlamaz.

Julia özelliklerini kullanarak hala globbing ve boru hatları yapabilirsiniz. Örneğin, yerleşik [`pipeline`](@ref) fonksiyonu, dış programları ve dosyaları zincirlemenize olanak tanır; bu, kabuk boruları ile benzerdir ve [Glob.jl package](https://github.com/vtjnash/Glob.jl) POSIX uyumlu globbing'i uygular.

Elbette, programları shell üzerinden çalıştırabilirsiniz, örneğin `run` fonksiyonuna bir shell ve bir komut dizesi geçirerek, örneğin ```run(`sh -c "ls > files.txt"`)``` Unix [Bourne shell](https://en.wikipedia.org/wiki/Bourne_shell) kullanmak için, ancak genellikle saf-Julia betiklerini tercih etmelisiniz, örneğin ```run(pipeline(`ls`, "files.txt"))```. Shell'den kaçınmamızın nedeni [shelling out sucks](https://julialang.org/blog/2012/03/shelling-out-sucks/): shell üzerinden süreç başlatmak yavaştır, özel karakterlerin alıntılanmasına karşı kırılgandır, kötü hata yönetimi vardır ve taşınabilirlik açısından sorunludur. (Python geliştiricileri [similar conclusion](https://www.python.org/dev/peps/pep-0324/#motivation) sonucuna vardılar.)

## Variables and Assignments

### Why am I getting `UndefVarError` from a simple loop?

Bunu şöyle bir şeyiniz olabilir:

```
x = 0
while x < 10
    x += 1
end
```

ve ve dikkat edin ki, etkileşimli bir ortamda (Julia REPL gibi) iyi çalışıyor, ancak bir betikte veya başka bir dosyada çalıştırmaya çalıştığınızda ```UndefVarError: `x` not defined``` hatası veriyor. Olan şey, Julia'nın genel olarak **yerel bir kapsamda küresel değişkenlere atama yaparken açık olmanızı** gerektirmesidir.

Burada, `x` bir global değişkendir, `while` bir [local scope](@ref scope-of-variables) tanımlar ve `x += 1` o yerel kapsamda bir global değişkene atamadır.

Yukarıda belirtildiği gibi, Julia (1.5 veya daha yeni sürüm) REPL'deki (ve birçok diğer etkileşimli ortamda) kod için `global` anahtar kelimesini atlamanıza izin verir, keşfi basitleştirmek için (örneğin, bir işlevden etkileşimli olarak çalıştırmak için kod kopyalayıp yapıştırmak). Ancak, dosyalardaki koda geçtiğinizde, Julia küresel değişkenler için daha disiplinli bir yaklaşım gerektirir. En az üç seçeneğiniz var:

1. Kodu bir işlev içine yerleştirin (böylece `x` bir işlevde *yerel* bir değişken olur). Genel olarak, işlevler kullanmak, küresel betikler yerine iyi bir yazılım mühendisliği uygulamasıdır (çevrimiçi "neden küresel değişkenler kötü" diye arama yaparak birçok açıklama bulabilirsiniz). Julia'da, küresel değişkenler de [slow](@ref man-performance-tips)'tür.
2. Wrap the code in a [`let`](@ref) block.  (This makes `x` a local variable within the `let ... end` statement, again eliminating the need for `global`).
3. Yerel kapsamda `x`'i atamadan önce açıkça `global` olarak işaretleyin, örneğin `global x += 1` yazın.

Daha fazla açıklama, [on soft scope](@ref on-soft-scope) bölümündeki kılavuzda bulunabilir.

## Functions

### I passed an argument `x` to a function, modified it inside that function, but on the outside, the variable `x` is still unchanged. Why?

Bir fonksiyonu şöyle çağırdığınızı varsayalım:

```jldoctest
julia> x = 10
10

julia> function change_value!(y)
           y = 17
       end
change_value! (generic function with 1 method)

julia> change_value!(x)
17

julia> x # x is unchanged!
10
```

Julia'da bir değişken `x`'in bağlaması, `x`'i bir işlevin argümanı olarak geçerek değiştirilemez. Yukarıdaki örnekte `change_value!(x)` çağrıldığında, `y` başlangıçta `x`'in değerine, yani `10`'a bağlı olarak yeni bir değişken olarak oluşturulur; ardından `y`, sabit `17`'ye yeniden bağlanırken, dış kapsamda bulunan `x` değişkeni dokunulmadan bırakılır.

Ancak, eğer `x` bir `Array` (veya başka bir *değiştirilebilir* tür) nesnesine bağlıysa. Fonksiyonun içinden, `x`'i bu Array'den "bağını çözemezsiniz", ancak içeriğini *değiştirebilirsiniz*. Örneğin:

```jldoctest
julia> x = [1,2,3]
3-element Vector{Int64}:
 1
 2
 3

julia> function change_array!(A)
           A[1] = 5
       end
change_array! (generic function with 1 method)

julia> change_array!(x)
5

julia> x
3-element Vector{Int64}:
 5
 2
 3
```

Burada `change_array!` adında bir fonksiyon oluşturduk; bu fonksiyon, geçirilen dizinin (çağrı yerinde `x` olarak bağlı ve fonksiyon içinde `A` olarak bağlı) ilk elemanına `5` atar. Fonksiyon çağrısından sonra, `x` hala aynı diziye bağlıdır, ancak o dizinin içeriği değişmiştir: `A` ve `x` değişkenleri, aynı değiştirilebilir `Array` nesnesine atıfta bulunan farklı bağlamalardır.

### Can I use `using` or `import` inside a function?

Hayır, bir fonksiyonun içinde `using` veya `import` ifadesine sahip olmanıza izin verilmez. Bir modülü içe aktarmak istiyorsanız ancak yalnızca belirli bir fonksiyon veya fonksiyon seti içinde sembollerini kullanmak istiyorsanız, iki seçeneğiniz vardır:

1. `import` kullanın:

    ```julia
    import Foo
    function bar(...)
        # ... refer to Foo symbols via Foo.baz ...
    end
    ```

    Bu, `Foo` modülünü yükler ve `Foo` modülüne atıfta bulunan bir `Foo` değişkeni tanımlar, ancak modülden mevcut ad alanına başka semboller ithal etmez. `Foo` sembollerine nitelikli adlarıyla `Foo.bar` vb. şeklinde atıfta bulunursunuz.
2. Modülünüzü bir fonksiyonla sarın:

    ```julia
    module Bar
    export bar
    using Foo
    function bar(...)
        # ... refer to Foo.baz as simply baz ....
    end
    end
    using Bar
    ```

    Bu, `Foo`'dan tüm sembolleri içe aktarır, ancak yalnızca `Bar` modülü içinde.

### What does the `...` operator do?

#### The two uses of the `...` operator: slurping and splatting

Birçok Julia yeni kullanıcısı `...` operatörünü kafa karıştırıcı buluyor. `...` operatörünü kafa karıştırıcı yapan şeylerden biri, bağlama bağlı olarak iki farklı anlama gelmesidir.

#### `...` combines many arguments into one argument in function definitions

Fonksiyon tanımları bağlamında, `...` operatörü birçok farklı argümanı tek bir argüman haline getirmek için kullanılır. Birçok farklı argümanı tek bir argüman haline getirmek için `...` kullanımına slurping denir:

```jldoctest
julia> function printargs(args...)
           println(typeof(args))
           for (i, arg) in enumerate(args)
               println("Arg #$i = $arg")
           end
       end
printargs (generic function with 1 method)

julia> printargs(1, 2, 3)
Tuple{Int64, Int64, Int64}
Arg #1 = 1
Arg #2 = 2
Arg #3 = 3
```

Eğer Julia, ASCII karakterlerini daha liberal bir şekilde kullanan bir dil olsaydı, yudumlama operatörü `...` yerine `<-...` olarak yazılabilirdi.

#### `...` splits one argument into many different arguments in function calls

`...` operatörünün bir fonksiyon tanımlarken birçok farklı argümanı tek bir argüman haline getirmek için kullanılmasına karşılık, `...` operatörü bir fonksiyon çağrısı bağlamında tek bir fonksiyon argümanının birçok farklı argümana ayrılmasını sağlamak için de kullanılır. Bu `...` kullanımına splatting denir:

```jldoctest
julia> function threeargs(a, b, c)
           println("a = $a::$(typeof(a))")
           println("b = $b::$(typeof(b))")
           println("c = $c::$(typeof(c))")
       end
threeargs (generic function with 1 method)

julia> x = [1, 2, 3]
3-element Vector{Int64}:
 1
 2
 3

julia> threeargs(x...)
a = 1::Int64
b = 2::Int64
c = 3::Int64
```

Eğer Julia, ASCII karakterlerini daha liberal bir şekilde kullanan bir dil olsaydı, splatting operatörü `...->` olarak yazılabilirdi.

### What is the return value of an assignment?

Operatör `=` her zaman sağ tarafı döndürür, bu nedenle:

```jldoctest
julia> function threeint()
           x::Int = 3.0
           x # returns variable x
       end
threeint (generic function with 1 method)

julia> function threefloat()
           x::Int = 3.0 # returns 3.0
       end
threefloat (generic function with 1 method)

julia> threeint()
3

julia> threefloat()
3.0
```

ve aynı şekilde:

```jldoctest
julia> function twothreetup()
           x, y = [2, 3] # assigns 2 to x and 3 to y
           x, y # returns a tuple
       end
twothreetup (generic function with 1 method)

julia> function twothreearr()
           x, y = [2, 3] # returns an array
       end
twothreearr (generic function with 1 method)

julia> twothreetup()
(2, 3)

julia> twothreearr()
2-element Vector{Int64}:
 2
 3
```

## Types, type declarations, and constructors

### [What does "type-stable" mean?](@id man-type-stability)

Bu, çıktının türünün girdilerin türlerinden tahmin edilebilir olduğu anlamına gelir. Özellikle, çıktının türünün girdilerin *değerlerine* bağlı olarak değişemeyeceği anlamına gelir. Aşağıdaki kod *tip kararlı* değildir:

```jldoctest
julia> function unstable(flag::Bool)
           if flag
               return 1
           else
               return 1.0
           end
       end
unstable (generic function with 1 method)
```

Bir `Int` ya da [`Float64`](@ref) döndürür, argümanının değerine bağlı olarak. Julia, bu fonksiyonun dönüş türünü derleme zamanında tahmin edemediğinden, onu kullanan herhangi bir hesaplama, her iki türdeki değerlerle başa çıkabilmelidir; bu da hızlı makine kodu üretmeyi zorlaştırır.

### [Why does Julia give a `DomainError` for certain seemingly-sensible operations?](@id faq-domain-errors)

Belirli işlemler matematiksel olarak mantıklı olsa da hatalara yol açar:

```jldoctest
julia> sqrt(-2.0)
ERROR: DomainError with -2.0:
sqrt was called with a negative real argument but will only return a complex result if called with a complex argument. Try sqrt(Complex(x)).
Stacktrace:
[...]
```

Bu davranış, tür kararlılığı gereksiniminin rahatsız edici bir sonucudur. [`sqrt`](@ref) durumunda, çoğu kullanıcı `sqrt(2.0)` ifadesinin gerçek bir sayı vermesini ister ve karmaşık sayı olan `1.4142135623730951 + 0.0im` üretirse mutsuz olur. `4d61726b646f776e2e436f64652822222c2022737172742229_40726566` fonksiyonu, yalnızca negatif bir sayı geçirildiğinde karmaşık değerli bir çıktıya geçecek şekilde yazılabilir (bu, bazı diğer dillerde `4d61726b646f776e2e436f64652822222c2022737172742229_40726566`'nın yaptığı gibi), ancak bu durumda sonuç [type-stable](@ref man-type-stability) olmayacak ve `4d61726b646f776e2e436f64652822222c2022737172742229_40726566` fonksiyonu kötü performans gösterecektir.

Bu ve diğer durumlarda, istediğiniz sonuca ulaşmak için sonucu temsil edebileceğiniz bir *çıkış türü* kabul etmeye istekli olduğunuzu ileten bir *giriş türü* seçerek sonuç alabilirsiniz:

```jldoctest
julia> sqrt(-2.0+0im)
0.0 + 1.4142135623730951im
```

### How can I constrain or compute type parameters?

The parameters of a [parametric type](@ref Parametric-Types) can hold either types or bits values, and the type itself chooses how it makes use of these parameters. For example, `Array{Float64, 2}` is parameterized by the type `Float64` to express its element type and the integer value `2` to express its number of dimensions.  When defining your own parametric type, you can use subtype constraints to declare that a certain parameter must be a subtype ([`<:`](@ref)) of some abstract type or a previous type parameter.  There is not, however, a dedicated syntax to declare that a parameter must be a *value* of a given type — that is, you cannot directly declare that a dimensionality-like parameter [`isa`](@ref) `Int` within the `struct` definition, for example.  Similarly, you cannot do computations (including simple things like addition or subtraction) on type parameters.  Instead, these sorts of constraints and relationships may be expressed through additional type parameters that are computed and enforced within the type's [constructors](@ref man-constructors).

Bir örnek olarak, düşünün

```julia
struct ConstrainedType{T,N,N+1} # NOTE: INVALID SYNTAX
    A::Array{T,N}
    B::Array{T,N+1}
end
```

kullanıcının üçüncü tür parametresinin her zaman ikinci tür parametresinin bir fazlası olmasını zorlamak istediği yer. Bu, [inner constructor method](@ref man-inner-constructor-methods) ile kontrol edilen açık bir tür parametresi ile uygulanabilir (diğer kontrollerle birleştirilebilir):

```julia
struct ConstrainedType{T,N,M}
    A::Array{T,N}
    B::Array{T,M}
    function ConstrainedType(A::Array{T,N}, B::Array{T,M}) where {T,N,M}
        N + 1 == M || throw(ArgumentError("second argument should have one more axis" ))
        new{T,N,M}(A, B)
    end
end
```

Bu kontrol genellikle *masrafsız*dır, çünkü derleyici geçerli somut türler için kontrolü atlayabilir. İkinci argüman da hesaplanıyorsa, bu hesaplamayı gerçekleştiren bir [outer constructor method](@ref man-outer-constructor-methods) sağlamanın avantajlı olması mümkündür:

```julia
ConstrainedType(A) = ConstrainedType(A, compute_B(A))
```

### [Why does Julia use native machine integer arithmetic?](@id faq-integer-arithmetic)

Julia, tam sayısal hesaplamalar için makine aritmetiği kullanır. Bu, `Int` değerlerinin aralığının sınırlı olduğu ve her iki uçta da sarıldığı anlamına gelir, bu nedenle tam sayıların toplama, çıkarma ve çarpma işlemleri taşma veya eksilme yapabilir, bu da başlangıçta bazı sonuçların rahatsız edici olmasına yol açabilir:

```jldoctest
julia> x = typemax(Int)
9223372036854775807

julia> y = x+1
-9223372036854775808

julia> z = -y
-9223372036854775808

julia> 2*z
0
```

Açıkça, bu durum matematiksel tam sayıların davranışından oldukça uzaktır ve bir yüksek seviyeli programlama dilinin bunu kullanıcıya açmasının ideal olmadığını düşünebilirsiniz. Ancak, verimlilik ve şeffaflığın ön planda olduğu sayısal çalışmalar için alternatifler daha kötüdür.

Bir alternatif olarak, her tam sayı işlemini taşma için kontrol etmek ve sonuçları [`Int128`](@ref) veya taşma durumunda [`BigInt`](@ref) gibi daha büyük tam sayı türlerine yükseltmek düşünülebilir. Ne yazık ki, bu her tam sayı işlemi üzerinde büyük bir yük getirir (bir döngü sayacını artırmayı düşünün) - aritmetik talimatlardan sonra çalışma zamanı taşma kontrolleri gerçekleştirmek ve potansiyel taşmaları ele almak için dallanma kodu yaymak gerektirir. Daha da kötüsü, bu, tam sayılarla ilgili her hesaplamanın tür açısından kararsız olmasına neden olur. Yukarıda belirttiğimiz gibi, [type-stability is crucial](@ref man-type-stability) etkili ve verimli kod üretimi için. Eğer tam sayı işlemlerinin sonuçlarının tam sayılar olacağına güvenemezseniz, C ve Fortran derleyicilerinin yaptığı gibi hızlı, basit kod üretmek imkansızdır.

Bu yaklaşımın bir varyasyonu, tür kararsızlığının görünümünü önlemek için `Int` ve [`BigInt`](@ref) türlerini tek bir hibrit tam sayı türünde birleştirmektir; bu tür, bir sonuç makine tam sayısının boyutuna sığmadığında içsel olarak temsilini değiştirir. Bu, yüzeysel olarak Julia kodu seviyesinde tür kararsızlığını önlese de, sorunu halının altına süpürmekte ve bu hibrit tam sayı türünü uygulayan C koduna aynı zorlukları yüklemektedir. Bu yaklaşım *çalıştırılabilir* hale getirilebilir ve birçok durumda oldukça hızlı hale getirilebilir, ancak birkaç dezavantajı vardır. Bir sorun, tam sayıların ve tam sayı dizilerinin bellek içindeki temsilinin C, Fortran ve yerel makine tam sayıları kullanan diğer dillerin doğal temsiliyle artık eşleşmemesidir. Bu nedenle, bu dillerle birlikte çalışabilmek için nihayetinde yerel tam sayı türlerini tanıtmamız gerekecektir. Sınırsız bir tam sayı temsili sabit bir bit sayısına sahip olamaz ve bu nedenle sabit boyutlu slotlara sahip bir dizide çevrimiçi olarak saklanamaz – büyük tam sayı değerleri her zaman ayrı yığın tahsis edilmiş depolama gerektirecektir. Ve elbette, kullanılan hibrit tam sayı uygulaması ne kadar zeki olursa olsun, her zaman performans tuzakları vardır – performansın beklenmedik bir şekilde düştüğü durumlar. Karmaşık temsil, C ve Fortran ile birlikte çalışabilirlik eksikliği, ek yığın depolama olmadan tam sayı dizilerini temsil etme yeteneği ve öngörülemeyen performans özellikleri, en zeki hibrit tam sayı uygulamalarını bile yüksek performanslı sayısal çalışmalar için kötü bir seçim haline getirir.

Hibrit tam sayılar kullanmak veya BigInt'lere terfi etmek yerine, en büyük tam sayı değerine ekleme yapıldığında değerin değişmediği ve en küçük tam sayı değerinden çıkarma yapıldığında da aynı şekilde değerin değişmediği doygun tam sayı aritmetiği kullanmak bir alternatiftir. Bu, tam olarak Matlab™'in yaptığıdır:

```
>> int64(9223372036854775807)

ans =

  9223372036854775807

>> int64(9223372036854775807) + 1

ans =

  9223372036854775807

>> int64(-9223372036854775808)

ans =

 -9223372036854775808

>> int64(-9223372036854775808) - 1

ans =

 -9223372036854775808
```

İlk bakışta, bu oldukça makul görünüyor çünkü 9223372036854775807, -9223372036854775808'den çok daha yakın ve tam sayılar hala C ve Fortran ile uyumlu bir şekilde sabit boyutta doğal bir şekilde temsil ediliyor. Ancak, doygun tam sayı aritmetiği derinlemesine sorunludur. İlk ve en bariz sorun, bu durumun makine tam sayı aritmetiğinin çalışma şekli olmamasıdır, bu nedenle doygun işlemleri uygulamak, her makine tam sayı işleminin ardından alt taşma veya taşma kontrolü yapmak ve sonucu uygun şekilde [`typemin(Int)`](@ref) veya [`typemax(Int)`](@ref) ile değiştirmek için talimatlar yaymak gerektirir. Bu, her tam sayı işlemini tek bir, hızlı bir talimattan altı talimata genişletir, muhtemelen dallanmaları da içerir. Ah! Ama daha da kötüleşiyor - doygun tam sayı aritmetiği birleşmeli değildir. Bu Matlab hesaplamasını düşünün:

```
>> n = int64(2)^62
4611686018427387904

>> n + (n - 1)
9223372036854775807

>> (n + n) - 1
9223372036854775806
```

Bu, birçok temel tam sayı algoritmasını yazmayı zorlaştırır çünkü birçok yaygın teknik, makine toplamasının taşma ile *birleşimli* olduğu gerçeğine dayanır. Julia'da `lo` ve `hi` tam sayı değerleri arasındaki orta noktayı bulmayı `(lo + hi) >>> 1` ifadesiyle düşünün:

```jldoctest
julia> n = 2^62
4611686018427387904

julia> (n + 2n) >>> 1
6917529027641081856
```

Görüyor musun? Hiçbir sorun yok. Bu, 2^62 ile 2^63 arasındaki doğru orta noktadır, `n + 2n` -4611686018427387904 olmasına rağmen. Şimdi bunu Matlab'ta dene:

```
>> (n + 2*n)/2

ans =

  4611686018427387904
```

Üzgünüm. Matlab'a bir `>>>` operatörü eklemek yardımcı olmaz, çünkü `n` ve `2n` eklenirken meydana gelen doygunluk, doğru orta noktayı hesaplamak için gerekli bilgiyi zaten yok etmiştir.

Sadece birleşim eksikliği, bunun gibi teknikler için güvenemeyen programcılar için talihsiz olmakla kalmaz, aynı zamanda derleyicilerin tam sayı aritmetiğini optimize etmek için yapmak isteyebileceği hemen hemen her şeyi de boşa çıkarır. Örneğin, Julia tam sayıları normal makine tam sayı aritmetiği kullandığı için, LLVM basit küçük fonksiyonları agresif bir şekilde optimize etme özgürlüğüne sahiptir, örneğin `f(k) = 5k-1`. Bu fonksiyonun makine kodu tam olarak şudur:

```julia-repl
julia> code_native(f, Tuple{Int})
  .text
Filename: none
  pushq %rbp
  movq  %rsp, %rbp
Source line: 1
  leaq  -1(%rdi,%rdi,4), %rax
  popq  %rbp
  retq
  nopl  (%rax,%rax)
```

Fonksiyonun gerçek gövdesi tek bir `leaq` talimatıdır; bu, tam olarak bir seferde tam sayı çarpma ve toplama işlemini hesaplar. Bu, `f` başka bir fonksiyona yerleştirildiğinde daha da faydalıdır:

```julia-repl
julia> function g(k, n)
           for i = 1:n
               k = f(k)
           end
           return k
       end
g (generic function with 1 methods)

julia> code_native(g, Tuple{Int,Int})
  .text
Filename: none
  pushq %rbp
  movq  %rsp, %rbp
Source line: 2
  testq %rsi, %rsi
  jle L26
  nopl  (%rax)
Source line: 3
L16:
  leaq  -1(%rdi,%rdi,4), %rdi
Source line: 2
  decq  %rsi
  jne L16
Source line: 5
L26:
  movq  %rdi, %rax
  popq  %rbp
  retq
  nop
```

`f` fonksiyonuna yapılan çağrı iç içe geçtiği için, döngü gövdesi sadece tek bir `leaq` talimatı haline gelir. Sonraki adımda, döngü yinelemelerinin sayısını sabit hale getirirsek neler olacağını düşünelim:

```julia-repl
julia> function g(k)
           for i = 1:10
               k = f(k)
           end
           return k
       end
g (generic function with 2 methods)

julia> code_native(g,(Int,))
  .text
Filename: none
  pushq %rbp
  movq  %rsp, %rbp
Source line: 3
  imulq $9765625, %rdi, %rax    # imm = 0x9502F9
  addq  $-2441406, %rax         # imm = 0xFFDABF42
Source line: 5
  popq  %rbp
  retq
  nopw  %cs:(%rax,%rax)
```

Çünkü derleyici, tam sayı toplama ve çarpmanın birleşimli olduğunu ve çarpmanın toplama göre dağıldığını bilir - bu, doygun aritmetik için geçerli değildir - bu nedenle döngüyü sadece bir çarpma ve bir toplama indirgemek için optimize edebilir. Doygun aritmetik, bu tür bir optimizasyonu tamamen boşa çıkarır çünkü birleşim ve dağıtım her döngü yinelemesinde başarısız olabilir ve başarısızlığın hangi yinelemede meydana geldiğine bağlı olarak farklı sonuçlar doğurabilir. Derleyici döngüyü açabilir, ancak birden fazla işlemi daha az eşdeğer işleme cebirsel olarak azaltamaz.

Tam sayısal aritmetiğin sessizce taşmasını önlemenin en makul alternatifi, her yerde kontrol edilen aritmetik yapmaktır; bu, toplama, çıkarma ve çarpma işlemleri taşma durumunda hata yükselterek, değer açısından doğru olmayan değerler üretir. Bu [blog post](https://danluu.com/integer-overflow/) bağlamında, Dan Luu bunu analiz ediyor ve bu yaklaşımın teorik olarak sahip olması gereken basit maliyetin aksine, derleyicilerin (LLVM ve GCC) ek taşma kontrolleri etrafında zarif bir şekilde optimize etmemesi nedeniyle önemli bir maliyetle sonuçlandığını buluyor. Gelecekte bu iyileşirse, Julia'da kontrol edilen tam sayı aritmetiğine varsayılan olarak geçmeyi düşünebiliriz, ancak şu anda taşma olasılığı ile yaşamak zorundayız.

Bu arada, taşma güvenli tam sayı işlemleri, [SaferIntegers.jl](https://github.com/JeffreySarnoff/SaferIntegers.jl) gibi harici kütüphanelerin kullanımıyla gerçekleştirilebilir. Daha önce belirtildiği gibi, bu kütüphanelerin kullanımı, kontrol edilen tam sayı türlerini kullanan kodun yürütme süresini önemli ölçüde artırır. Ancak, sınırlı kullanım için bu, tüm tam sayı işlemleri için kullanıldığında olduğundan çok daha az bir sorun teşkil eder. Tartışmanın durumunu [here](https://github.com/JuliaLang/julia/issues/855) adresinden takip edebilirsiniz.

### What are the possible causes of an `UndefVarError` during remote execution?

Hata mesajının belirttiği gibi, bir uzak düğümdeki `UndefVarError` hatasının hemen hemen bir nedeni, o isimle bir bağlamanın mevcut olmamasıdır. Olası bazı nedenleri keşfedelim.

```julia-repl
julia> module Foo
           foo() = remotecall_fetch(x->x, 2, "Hello")
       end

julia> Foo.foo()
ERROR: On worker 2:
UndefVarError: `Foo` not defined in `Main`
Stacktrace:
[...]
```

Kapatma `x->x`, `Foo`'ya bir referans taşır ve `Foo` node 2'de mevcut olmadığından, bir `UndefVarError` hatası fırlatılır.

Modüller dışında `Main` altında bulunan global değişkenler, uzak düğüme değer olarak serileştirilmez. Sadece bir referans gönderilir. Global bağlamalar oluşturan fonksiyonlar ( `Main` dışında) daha sonra bir `UndefVarError` hatası fırlatabilir.

```julia-repl
julia> @everywhere module Foo
           function foo()
               global gvar = "Hello"
               remotecall_fetch(()->gvar, 2)
           end
       end

julia> Foo.foo()
ERROR: On worker 2:
UndefVarError: `gvar` not defined in `Main.Foo`
Stacktrace:
[...]
```

Yukarıdaki örnekte, `@everywhere module Foo` `Foo`'yu tüm düğümlerde tanımladı. Ancak `Foo.foo()` çağrısı yerel düğümde yeni bir global bağlama `gvar` oluşturdu, ancak bu düğüm 2'de bulunmadığı için bir `UndefVarError` hatası meydana geldi.

Not edin ki bu, `Main` modülü altında oluşturulan global değişkenler için geçerli değildir. `Main` modülü altında oluşturulan global değişkenler serileştirilir ve uzak düğümde `Main` altında yeni bağlamalar oluşturulur.

```julia-repl
julia> gvar_self = "Node1"
"Node1"

julia> remotecall_fetch(()->gvar_self, 2)
"Node1"

julia> remotecall_fetch(varinfo, 2)
name          size summary
––––––––– –––––––– –––––––
Base               Module
Core               Module
Main               Module
gvar_self 13 bytes String
```

Bu, `function` veya `struct` bildirimlerine uygulanmaz. Ancak, aşağıda görülebileceği gibi, küresel değişkenlere bağlı anonim fonksiyonlar serileştirilir.

```julia-repl
julia> bar() = 1
bar (generic function with 1 method)

julia> remotecall_fetch(bar, 2)
ERROR: On worker 2:
UndefVarError: `#bar` not defined in `Main`
[...]

julia> anon_bar  = ()->1
(::#21) (generic function with 1 method)

julia> remotecall_fetch(anon_bar, 2)
1
```

## Troubleshooting "method not matched": parametric type invariance and `MethodError`s

### Why doesn't it work to declare `foo(bar::Vector{Real}) = 42` and then call `foo([1])`?

Görmeyi denerseniz, sonuç bir `MethodError` olacaktır:

```jldoctest
julia> foo(x::Vector{Real}) = 42
foo (generic function with 1 method)

julia> foo([1])
ERROR: MethodError: no method matching foo(::Vector{Int64})
The function `foo` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  foo(!Matched::Vector{Real})
   @ Main none:1

Stacktrace:
[...]
```

Bu, `Vector{Real}`'ın `Vector{Int}`'in bir süper türü olmamasındandır! Bu sorunu, `foo(bar::Vector{T}) where {T<:Real}` gibi bir şeyle çözebilirsiniz (veya fonksiyonun gövdesinde statik parametre `T`'ye ihtiyaç yoksa kısa form `foo(bar::Vector{<:Real})` ile). `T` bir joker karakterdir: önce bunun Real'in bir alt türü olması gerektiğini belirtirsiniz, ardından fonksiyonun o türdeki elemanlarla bir Vektör aldığını belirtirsiniz.

Bu aynı sorun, yalnızca `Vector` için değil, herhangi bir bileşik tür `Comp` için geçerlidir. Eğer `Comp` türünde bir `Y` türünde parametre tanımlanmışsa, o zaman `X<:Y` türünde bir parametreye sahip başka bir tür `Comp2`, `Comp`'in bir alt türü değildir. Bu, tür-invazansıdır (aksine, Tuple parametrelerinde tür-kovaryandır). Daha fazla açıklama için [Parametric Composite Types](@ref man-parametric-composite-types)'e bakın.

### Why does Julia use `*` for string concatenation? Why not `+` or something else?

[main argument](@ref man-concatenation) ile `+` arasındaki fark, dize birleştirmenin komütatif olmamasıdır, oysa `+` genellikle komütatif bir operatör olarak kullanılır. Julia topluluğu, diğer dillerin farklı operatörler kullandığını kabul etse de ve `*` bazı kullanıcılar için tanıdık olmayabilir, belirli cebirsel özellikleri iletmekte.

Not edin ki, `string(...)` kullanarak dizeleri (ve dizeye dönüştürülen diğer değerleri) birleştirebilirsiniz; benzer şekilde, dizeleri tekrar etmek için `repeat` kullanılabilir. [interpolation syntax](@ref string-interpolation) dizeleri oluşturmak için de yararlıdır.

## Packages and Modules

### What is the difference between "using" and "import"?

`using` ve `import` arasında birkaç fark vardır (bkz. [Modules section](https://docs.julialang.org/en/v1/manual/modules/#modules)), ancak ilk bakışta sezgisel görünmeyen ve yüzeyde (yani sözdizimsel olarak) çok önemsiz gibi görünen önemli bir fark vardır. `using` ile modülleri yüklerken, `Foo` modülünün `bar` fonksiyonunu yeni bir yöntemle genişletmek için `function Foo.bar(...` demeniz gerekir, ancak `import Foo.bar` ile yalnızca `function bar(...` demeniz yeterlidir ve bu otomatik olarak `Foo` modülünün `bar` fonksiyonunu genişletir.

Bu, ayrı bir sözdizimi verilmiş olmasının önemli bir nedeni, var olduğunu bilmediğiniz bir işlevi yanlışlıkla genişletmek istememenizdir; çünkü bu kolayca bir hataya neden olabilir. Bu, genellikle bir dize veya tam sayı gibi yaygın bir türü alan bir yöntemle gerçekleşir, çünkü hem siz hem de diğer modül, böyle yaygın bir türü işlemek için bir yöntem tanımlayabilirsiniz. `import` kullanırsanız, diğer modülün `bar(s::AbstractString)` uygulamasını, tamamen farklı bir şey yapabilecek olan yeni uygulamanızla değiştirmiş olursunuz (ve bu, Foo modülündeki diğer işlevlerin bar'ı çağırmaya bağımlı olan tüm/pek çok gelecekteki kullanımını bozabilir).

## Nothingness and missing values

### [How does "null", "nothingness" or "missingness" work in Julia?](@id faq-nothing)

Diğer birçok dilin (örneğin, C ve Java) aksine, Julia nesneleri varsayılan olarak "null" olamaz. Bir referans (değişken, nesne alanı veya dizi elemanı) başlatılmamışsa, ona erişmek hemen bir hata fırlatır. Bu durum, [`isdefined`](@ref) veya [`isassigned`](@ref Base.isassigned) fonksiyonları kullanılarak tespit edilebilir.

Bazı fonksiyonlar yalnızca yan etkileri için kullanılır ve bir değer döndürmeleri gerekmez. Bu durumlarda, `nothing` değerini döndürme geleneği vardır; bu, `Nothing` türünde yalnızca bir nesne olan bir singleton nesnedir. Bu, alanı olmayan sıradan bir türdür; bu geleneğin dışında özel bir durumu yoktur ve REPL bunun için hiçbir şey yazdırmaz. Aksi takdirde bir değeri olmayan bazı dil yapıları da `nothing` döndürür; örneğin `if false; end`.

Durumlarda `T` türünde bir `x` değerinin yalnızca bazen mevcut olduğu durumlar için, `Union{T, Nothing}` türü, işlev argümanları, nesne alanları ve dizi eleman türleri için kullanılabilir; bu, diğer dillerde [`Nullable`, `Option` or `Maybe`](https://en.wikipedia.org/wiki/Nullable_type) ile eşdeğerdir. Değerin kendisi `nothing` olabiliyorsa (özellikle `T` `Any` olduğunda), `Union{Some{T}, Nothing}` türü daha uygundur; çünkü bu durumda `x == nothing` bir değerin yokluğunu, `x == Some(nothing)` ise `nothing` değerine eşit bir değerin varlığını gösterir. [`something`](@ref) işlevi, `Some` nesnelerini açmayı ve `nothing` argümanları yerine varsayılan bir değer kullanmayı sağlar. Derleyicinin `Union{T, Nothing}` argümanları veya alanları ile çalışırken verimli kod üretebildiğini unutmayın.

To represent missing data in the statistical sense (`NA` in R or `NULL` in SQL), use the [`missing`](@ref) object. See the [`Missing Values`](@ref missing) section for more details.

Bazı dillerde, boş demet (`()`) yokluğun kanonik biçimi olarak kabul edilir. Ancak, Julia'da bunun sıfır değer içeren sıradan bir demet olarak düşünülmesi en iyisidir.

Boş (veya "alt") tür, `Union{}` (boş bir birleşim türü) olarak yazılır, değerleri ve alt türleri (kendisi hariç) olmayan bir türdür. Genel olarak bu türü kullanmanıza gerek kalmayacaktır.

## Memory

### Why does `x += y` allocate memory when `x` and `y` are arrays?

Julia'da, `x += y` düşürme sırasında `x = x + y` ile değiştirilir. Diziler için bu, sonucu `x` ile aynı bellek konumuna depolamak yerine, sonucu depolamak için yeni bir dizi tahsis edildiği anlamına gelir. `x`'i değiştirmeyi tercih ediyorsanız, her bir öğeyi ayrı ayrı güncellemek için `x .+= y` kullanın.

Bu davranış bazılarını şaşırtabilirken, seçim kasıtlıdır. Ana neden, yaratıldıktan sonra değerini değiştiremeyen değişmez nesnelerin Julia'da bulunmasıdır. Gerçekten de, bir sayı değişmez bir nesnedir; `x = 5; x += 1` ifadeleri `5`'in anlamını değiştirmez, `x`'e bağlı olan değeri değiştirir. Değişmez bir nesne için, değeri değiştirmek için tek yol onu yeniden atamaktır.

Biraz daha açmak için, aşağıdaki fonksiyonu düşünün:

```julia
function power_by_squaring(x, n::Int)
    ispow2(n) || error("This implementation only works for powers of 2")
    while n >= 2
        x *= x
        n >>= 1
    end
    x
end
```

`x = 5; y = power_by_squaring(x, 4)` çağrısından sonra beklenen sonucu alırsınız: `x == 5 && y == 625`. Ancak, şimdi `*=`, matrislerle kullanıldığında, sol tarafı değiştirecek şekilde davrandığını varsayalım. İki sorun olacaktır:

  * Genel kare matrisler için, `A = A*B` geçici depolama olmadan uygulanamaz: `A[1,1]` sol tarafta hesaplanıp depolandıktan sonra sağ tarafta kullanılmadan önce tamamlanmamış olur.
  * Diyelim ki, hesaplama için geçici bir alan ayırmaya istekliydiniz (bu, `*=` işleminin yerinde çalışmasını sağlamanın çoğu amacını ortadan kaldırır); `x`'in değiştirilebilirliğinden yararlanırsanız, bu fonksiyon değiştirilebilir ve değiştirilemez girdiler için farklı davranır. Özellikle, değiştirilemez `x` için, çağrıdan sonra (genel olarak) `y != x` olur, ancak değiştirilebilir `x` için `y == x` olur.

Çünkü genel programlamayı desteklemenin, diğer yollarla (örneğin, yayılma veya açık döngüler kullanarak) elde edilebilecek potansiyel performans optimizasyonlarından daha önemli olduğu düşünülmektedir, `+=` ve `*=` gibi operatörler yeni değerler bağlayarak çalışır.

## [Asynchronous IO and concurrent synchronous writes](@id faq-async-io)

### Why do concurrent writes to the same stream result in inter-mixed output?

Akış I/O API'si senkron olsa da, temel uygulama tamamen asenkron bir yapıya sahiptir.

Lütfen çevirmemi istediğiniz Markdown içeriğini paylaşın.

```jldoctest
julia> @sync for i in 1:3
           @async write(stdout, string(i), " Foo ", " Bar ")
       end
123 Foo  Foo  Foo  Bar  Bar  Bar
```

Bu, `write` çağrısı senkron olduğu için, her bir argümanın yazılması, I/O'nun o kısmının tamamlanmasını beklerken diğer görevlere geçiş yapmasından kaynaklanıyor.

`print` ve `println` çağrısı sırasında akışı "kilitler". Sonuç olarak, yukarıdaki örnekte `write`'i `println` ile değiştirmek şuna yol açar:

```jldoctest
julia> @sync for i in 1:3
           @async println(stdout, string(i), " Foo ", " Bar ")
       end
1 Foo  Bar
2 Foo  Bar
3 Foo  Bar
```

Yazılarınızı `ReentrantLock` ile şu şekilde kilitleyebilirsiniz:

```jldoctest
julia> l = ReentrantLock();

julia> @sync for i in 1:3
           @async begin
               lock(l)
               try
                   write(stdout, string(i), " Foo ", " Bar ")
               finally
                   unlock(l)
               end
           end
       end
1 Foo  Bar 2 Foo  Bar 3 Foo  Bar
```

## Arrays

### [What are the differences between zero-dimensional arrays and scalars?](@id faq-array-0dim)

Sıfır boyutlu diziler `Array{T,0}` biçimindeki dizilerdir. Skalarlar gibi davranırlar, ancak önemli farklılıklar vardır. Genel dizi tanımına göre mantıklı bir özel durum oldukları için özel bir şekilde anılmayı hak ediyorlar, ancak başlangıçta biraz sezgisel olmayabilirler. Aşağıdaki satır bir sıfır boyutlu dizi tanımlar:

```
julia> A = zeros()
0-dimensional Array{Float64,0}:
0.0
```

Bu örnekte, `A` bir öğe içeren değiştirilebilir bir konteynerdir; bu öğe `A[] = 1.0` ile ayarlanabilir ve `A[]` ile alınabilir. Tüm sıfır boyutlu dizilerin aynı boyutu vardır (`size(A) == ()`) ve uzunluğu (`length(A) == 1`) vardır. Özellikle, sıfır boyutlu diziler boş değildir. Eğer bunu sezgisel bulmuyorsanız, Julia'nın tanımını anlamanıza yardımcı olabilecek bazı fikirler burada.

  * Sıfır boyutlu diziler, vektörün "doğru" ve matrisin "düzlem"ine karşılık gelir. Tıpkı bir doğrunun alanı olmaması (ama yine de bir şeyler kümesini temsil etmesi) gibi, bir noktanın da uzunluğu veya herhangi bir boyutu yoktur (ama yine de bir şeyi temsil eder).
  * `prod(())`'yi 1 olarak tanımlıyoruz ve bir dizideki toplam eleman sayısı boyutların çarpımıdır. Sıfır boyutlu bir dizinin boyutu `()`'dur ve bu nedenle uzunluğu `1`'dir.
  * Sıfır boyutlu diziler, indeksleme yapabileceğiniz herhangi bir boyuta sahip değildir - sadece `A[]` şeklindedirler. Diğer tüm dizi boyutları için geçerli olan "son bir" kuralını onlara da uygulayabiliriz, bu nedenle onları gerçekten `A[1]`, `A[1,1]` vb. şeklinde indeksleyebilirsiniz; [Omitted and extra indices](@ref)'ya bakın.

Ayrıca, sıradan skalarlar ile olan farkları anlamak da önemlidir. Skalarlar değiştirilemeyen konteynerlerdir (her ne kadar yine de yinelemeli olsalar ve `length`, `getindex` gibi şeyleri tanımlasalar da, *örneğin* `1[] == 1`). Özellikle, `x = 0.0` bir skalar olarak tanımlandığında, değerini `x[] = 1.0` ile değiştirmeye çalışmak bir hatadır. Bir skalar `x`, onu içeren sıfır boyutlu bir diziye `fill(x)` ile dönüştürülebilir ve tersine, bir sıfır boyutlu dizi `a`, içindeki skalar değere `a[]` ile dönüştürülebilir. Bir diğer fark, bir skalar, `2 * rand(2,2)` gibi lineer cebir işlemlerine katılabilirken, sıfır boyutlu bir dizi ile benzer bir işlem `fill(2) * rand(2,2)` bir hatadır.

### Why are my Julia benchmarks for linear algebra operations different from other languages?

Basit lineer cebir yapı taşlarının basit kıyaslamalarını bulabilirsiniz.

```julia
using BenchmarkTools
A = randn(1000, 1000)
B = randn(1000, 1000)
@btime $A \ $B
@btime $A * $B
```

diğer dillerle, örneğin Matlab veya R ile karşılaştırıldığında farklı olabilir.

Bu tür işlemler, ilgili BLAS fonksiyonlarının çok ince sarmalayıcıları olduğu için, tutarsızlığın nedeni muhtemelen şudur:

1. her dilin kullandığı BLAS kütüphanesi,
2. eşzamanlı iş parçacıklarının sayısı.

Julia, kendi OpenBLAS kopyasını derler ve şu anda iş parçacıkları `8` (veya çekirdek sayınız) ile sınırlıdır.

OpenBLAS ayarlarını değiştirmek veya Julia'yı farklı bir BLAS kütüphanesi ile derlemek, örneğin [Intel MKL](https://software.intel.com/en-us/mkl), performans iyileştirmeleri sağlayabilir. Julia'nın lineer cebirinin OpenBLAS yerine Intel MKL BLAS ve LAPACK kullanmasını sağlayan [MKL.jl](https://github.com/JuliaComputing/MKL.jl) paketini kullanabilir veya bunu manuel olarak nasıl ayarlayacağınıza dair öneriler için tartışma forumunu arayabilirsiniz. Intel MKL'nın Julia ile birlikte paketlenemeyeceğini, çünkü açık kaynak olmadığını unutmayın.

## Computing cluster

### How do I manage precompilation caches in distributed file systems?

Julia yüksek performanslı hesaplama (HPC) tesislerinde paylaşılan dosya sistemleri ile kullanıldığında, paylaşılan bir depo kullanılması önerilir (bu, [`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH) ortam değişkeni aracılığıyla yapılır). Julia v1.10'dan itibaren, işlevsel olarak benzer işçilerde birden fazla Julia süreci aynı depoyu kullanarak pidfile kilitleri aracılığıyla koordine olacak ve yalnızca bir süreç önceden derleme yaparken diğerleri bekleyecektir. Önceden derleme süreci, sürecin önceden derleme yaptığını veya başka bir sürecin önceden derleme yapmasını beklediğini gösterecektir. Etkileşimli olmayan durumlarda mesajlar `@debug` aracılığıyla iletilir.

Ancak, ikili kodun önbelleğe alınması nedeniyle, v1.9'dan itibaren önbellek reddi daha katı hale geldi ve kullanıcıların HPC ortamında kullanılabilir tek bir önbellek elde etmek için [`JULIA_CPU_TARGET`](@ref JULIA_CPU_TARGET) ortam değişkenini uygun şekilde ayarlamaları gerekebilir.

## Julia Releases

### Do I want to use the Stable, LTS, or nightly version of Julia?

Julia'nın Stabil sürümü, Julia'nın en son yayımlanan sürümüdür; bu, çoğu kişinin çalıştırmak isteyeceği sürümdür. En son özellikleri, geliştirilmiş performans dahil olmak üzere içerir. Julia'nın Stabil sürümü, [SemVer](https://semver.org/) ile v1.x.y olarak sürümlendirilmiştir. Julia'nın yeni bir Stabil sürümüne karşılık gelen yeni bir küçük sürümü, birkaç haftalık test süresinin ardından yaklaşık her 4-5 ayda bir yapılmaktadır. LTS sürümünün aksine, Stabil sürüm normalde başka bir Stabil sürüm yayımlandıktan sonra hata düzeltmeleri almayacaktır. Ancak, bir sonraki Stabil sürüme yükseltme her zaman mümkün olacaktır, çünkü Julia v1.x'in her sürümü, daha önceki sürümler için yazılmış kodları çalıştırmaya devam edecektir.

Julia'nın çok stabil bir kod tabanı arıyorsanız LTS (Uzun Süreli Destek) sürümünü tercih edebilirsiniz. Mevcut LTS sürümü, SemVer'e göre v1.6.x olarak sürümlendirilmiştir; bu dal, yeni bir LTS dalı seçilene kadar hata düzeltmeleri almaya devam edecektir. Bu noktada, v1.6.x serisi düzenli hata düzeltmeleri almayacak ve en muhafazakar kullanıcılar dışında herkesin yeni LTS sürüm serisine geçmesi önerilecektir. Bir paket geliştiricisi olarak, paketinizin kullanılabilirliğini artırmak için LTS sürümü için geliştirme yapmayı tercih edebilirsiniz. SemVer'e göre, v1.0 için yazılan kod, tüm gelecekteki LTS ve Stabil sürümlerle çalışmaya devam edecektir. Genel olarak, LTS'yi hedeflese bile, en son Stabil sürümde kod geliştirebilir ve çalıştırabilirsiniz; böylece geliştirilmiş performanstan yararlanabilirsiniz; yeter ki yeni özellikler (eklenen kütüphane fonksiyonları veya yeni yöntemler gibi) kullanmaktan kaçının.

Julia'nın en son güncellemelerinden yararlanmak istiyorsanız ve bugün mevcut olan sürümün zaman zaman çalışmamasını umursamıyorsanız, gece sürümünü tercih edebilirsiniz. İsimden de anlaşılacağı gibi, gece sürümüne yapılan sürümler yaklaşık her gece (inşa altyapısının kararlılığına bağlı olarak) yapılmaktadır. Genel olarak, gece sürümleri kullanmak için oldukça güvenlidir—kodunuz alev almaz. Ancak, zaman zaman geri dönüşler ve daha kapsamlı ön sürüm testleri yapılmadan bulunmayacak sorunlar olabilir. Kullanım durumunuzu etkileyen böyle geri dönüşlerin, bir sürüm yapılmadan önce yakalanmasını sağlamak için gece sürümü ile test etmek isteyebilirsiniz.

Son olarak, Julia'yı kendiniz kaynak kodundan derlemeyi de düşünebilirsiniz. Bu seçenek, komut satırında rahat olan veya öğrenmeye ilgi duyan bireyler için özellikle uygundur. Eğer bu tanım size uyuyorsa, [guidelines for contributing](https://github.com/JuliaLang/julia/blob/master/CONTRIBUTING.md) okumakla da ilgilenebilirsiniz.

Bu indirme türlerinin her birine ait bağlantılar, [https://julialang.org/downloads/](https://julialang.org/downloads/) adresindeki indirme sayfasında bulunabilir. Tüm Julia sürümlerinin tüm platformlar için mevcut olmadığını unutmayın.

### How can I transfer the list of installed packages after updating my version of Julia?

Her bir küçük sürümün kendi varsayılan [environment](https://docs.julialang.org/en/v1/manual/code-loading/#Environments-1) vardır. Sonuç olarak, yeni bir Julia küçük sürümü yüklediğinizde, önceki küçük sürümle eklediğiniz paketler varsayılan olarak mevcut olmayacaktır. Belirli bir julia sürümü için ortam, `.julia/environments/` içindeki sürüm numarasına uyan bir klasörde bulunan `Project.toml` ve `Manifest.toml` dosyalarıyla tanımlanır; örneğin, `.julia/environments/v1.3`.

Eğer yeni bir küçük sürüm olan Julia `1.4`'ü kurar ve varsayılan ortamında önceki bir sürümde (örneğin `1.3`) bulunan aynı paketleri kullanmak isterseniz, `1.3` klasöründeki `Project.toml` dosyasının içeriğini `1.4` klasörüne kopyalayabilirsiniz. Ardından, yeni Julia sürümünde bir oturum açarak "paket yönetim modu"na geçmek için `]` tuşuna basın ve [`instantiate`](https://julialang.github.io/Pkg.jl/v1/api/#Pkg.instantiate) komutunu çalıştırın.

Bu işlem, kopyalanan dosyadan hedef Julia sürümüyle uyumlu bir dizi uygulanabilir paketi çözecek ve uygun olduğunda bunları yükleyecek veya güncelleyecektir. Sadece paketler setini değil, aynı zamanda önceki Julia sürümünde kullandığınız sürümleri de yeniden oluşturmak istiyorsanız, `instantiate` Pkg komutunu çalıştırmadan önce `Manifest.toml` dosyasını da kopyalamalısınız. Ancak, paketlerin Julia sürümünü değiştirmekten etkilenebilecek uyumluluk kısıtlamaları tanımlayabileceğini unutmayın, bu nedenle `1.3` sürümünde sahip olduğunuz tam sürüm seti `1.4` için çalışmayabilir.
