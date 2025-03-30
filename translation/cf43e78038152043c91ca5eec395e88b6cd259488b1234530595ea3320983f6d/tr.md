# [Performance Tips](@id man-performance-tips)

Aşağıdaki bölümlerde, Julia kodunuzun mümkün olan en hızlı şekilde çalışmasına yardımcı olabilecek birkaç tekniği kısaca gözden geçireceğiz.

## Performance critical code should be inside a function

Herhangi bir performans açısından kritik olan kod bir fonksiyonun içinde olmalıdır. Fonksiyonların içindeki kod, Julia'nın derleyicisinin çalışma şekli nedeniyle genellikle üst düzey koddan çok daha hızlı çalışır.

Fonksiyonların kullanımı yalnızca performans için önemli değildir: fonksiyonlar daha yeniden kullanılabilir ve test edilebilir, ayrıca hangi adımların yapıldığını ve bunların girdileri ile çıktılarının ne olduğunu netleştirir, [Write functions, not just scripts](@ref) ayrıca Julia'nın Stil Kılavuzu'nda bir öneridir.

Fonksiyonlar, doğrudan küresel değişkenler üzerinde işlem yapmak yerine argümanlar almalıdır, bir sonraki noktaya bakın.

## Avoid untyped global variables

Bir tür belirtilmemiş global değişkenin değeri herhangi bir noktada değişebilir, bu da türünün değişmesine yol açabilir. Bu, derleyicinin global değişkenler kullanan kodu optimize etmesini zorlaştırır. Bu, tür değerli değişkenler için de geçerlidir, yani global düzeydeki tür takma adları. Değişkenler mümkün olduğunca yerel olmalı veya fonksiyonlara argüman olarak geçirilmelidir.

Küresel adların sıklıkla sabitler olduğunu ve bunları bu şekilde tanımlamanın performansı büyük ölçüde artırdığını buluyoruz:

```julia
const DEFAULT_VAL = 0
```

Eğer bir global her zaman aynı türde biliniyorsa, [the type should be annotated](@ref man-typed-globals).

Kullanılmamış global değişkenlerin türleri, kullanıldığı noktada türlerini belirterek optimize edilebilir:

```julia
global x = rand(1000)

function loop_over_global()
    s = 0.0
    for i in x::Vector{Float64}
        s += i
    end
    return s
end
```

Fonksiyonlara argüman geçmek daha iyi bir stildir. Bu, daha yeniden kullanılabilir kodlar oluşturur ve girdilerin ve çıktının ne olduğunu netleştirir.

!!! note
    Tüm kod REPL'de global kapsamda değerlendirilir, bu nedenle en üst düzeyde tanımlanan ve atanan bir değişken **global** bir değişken olacaktır. Modüller içinde en üst düzey kapsamda tanımlanan değişkenler de globaldir.


REPL oturumunda:

```julia-repl
julia> x = 1.0
```

eşittir:

```julia-repl
julia> global x = 1.0
```

bu nedenle daha önce tartışılan tüm performans sorunları geçerlidir.

## Measure performance with [`@time`](@ref) and pay attention to memory allocation

Performans ölçmek için yararlı bir araç, [`@time`](@ref) makrosudur. Burada yukarıdaki küresel değişkenle örneği tekrar ediyoruz, ancak bu sefer tür açıklaması kaldırılmıştır:

```jldoctest; setup = :(using Random; Random.seed!(1234)), filter = r"[0-9\.]+ seconds \(.*?\)"
julia> x = rand(1000);

julia> function sum_global()
           s = 0.0
           for i in x
               s += i
           end
           return s
       end;

julia> @time sum_global()
  0.011539 seconds (9.08 k allocations: 373.386 KiB, 98.69% compilation time)
523.0007221951678

julia> @time sum_global()
  0.000091 seconds (3.49 k allocations: 70.156 KiB)
523.0007221951678
```

İlk çağrıda (`@time sum_global()`) fonksiyon derlenir. (Eğer bu oturumda [`@time`](@ref)'yı henüz kullanmadıysanız, zamanlama için gerekli olan fonksiyonlar da derlenecektir.) Bu çalışmanın sonuçlarını ciddiye almamalısınız. İkinci çalışmada, zamanın raporlanmasının yanı sıra, önemli miktarda bellek tahsis edildiğini de belirtmiştir. Burada sadece 64-bit float'lardan oluşan bir vektördeki tüm elemanların toplamını hesaplıyoruz, bu nedenle (yığın) bellek tahsis etmeye gerek olmamalıdır.

`@time` raporlarının özellikle *yığın* tahsisatlarını bildirdiğini netleştirmeliyiz; bu genellikle değişken nesneler veya değişken boyutlu konteynerler (örneğin `Array` veya `Dict`, dizeler veya yalnızca çalışma zamanında bilinen "tip-istikrarsız" nesneler) oluşturmak/büyütmek için gereklidir. Bu tür bellek bloklarını tahsis etmek (veya serbest bırakmak) libc'ye (örneğin C'de `malloc` aracılığıyla) pahalı bir işlev çağrısı gerektirebilir ve bunlar çöp toplama için izlenmelidir. Buna karşılık, sayılar (bignum'lar hariç), demetler ve değişmez `struct`lar gibi değişmez değerler çok daha ucuz bir şekilde saklanabilir; örneğin yığın veya CPU kayıt belleğinde, bu nedenle "tahsis etme" performans maliyeti hakkında genellikle endişelenmezsiniz.

Beklenmedik bellek tahsisi genellikle kodunuzda bir sorun olduğunun işareti olup, genellikle tür kararlılığı ile veya birçok küçük geçici dizi oluşturma ile ilgili bir sorundur. Sonuç olarak, tahsisin yanı sıra, fonksiyonunuz için üretilen kodun da oldukça optimal olmaması muhtemeldir. Bu tür belirtileri ciddiye alın ve aşağıdaki tavsiyeleri takip edin.

Bu özel durumda, bellek tahsisi, `x` adlı tür-istikrarsız bir global değişkenin kullanımından kaynaklanmaktadır, bu nedenle eğer `x`'i fonksiyona bir argüman olarak geçirirsek, artık bellek tahsis etmez (aşağıda rapor edilen kalan tahsis, global kapsamda `@time` makrosunun çalıştırılmasından kaynaklanmaktadır) ve ilk çağrıdan sonra önemli ölçüde daha hızlıdır:

```jldoctest sumarg; setup = :(using Random; Random.seed!(1234)), filter = r"[0-9\.]+ seconds \(.*?\)"
julia> x = rand(1000);

julia> function sum_arg(x)
           s = 0.0
           for i in x
               s += i
           end
           return s
       end;

julia> @time sum_arg(x)
  0.007551 seconds (3.98 k allocations: 200.548 KiB, 99.77% compilation time)
523.0007221951678

julia> @time sum_arg(x)
  0.000006 seconds (1 allocation: 16 bytes)
523.0007221951678
```

Görülen 1 tahsis, `@time` makrosunun kendisinin global kapsamda çalıştırılmasından kaynaklanmaktadır. Eğer zamanlamayı bir fonksiyonda çalıştırırsak, gerçekten de hiçbir tahsisin yapılmadığını görebiliriz:

```jldoctest sumarg; filter = r"[0-9\.]+ seconds"
julia> time_sum(x) = @time sum_arg(x);

julia> time_sum(x)
  0.000002 seconds
523.0007221951678
```

Bazı durumlarda, işlevinizin çalışması sırasında bellek ayırması gerekebilir ve bu, yukarıdaki basit resmi karmaşıklaştırabilir. Bu tür durumlarda, sorunları teşhis etmek için aşağıdaki [tools](@ref tools)'lerden birini kullanmayı veya bellek ayırmayı algoritmik yönlerinden ayıran bir işlev sürümü yazmayı düşünün (bkz. [Pre-allocating outputs](@ref)).

!!! note
    Daha ciddi kıyaslamalar için, gürültüyü azaltmak amacıyla fonksiyonu birden fazla kez değerlendiren [BenchmarkTools.jl](https://github.com/JuliaCI/BenchmarkTools.jl) paketini dikkate almayı düşünün.


## [Tools](@id tools)

Julia ve paket ekosistemi, sorunları teşhis etmenize ve kodunuzun performansını artırmanıza yardımcı olabilecek araçlar içerir:

  * [Profiling](@ref) kodunuzun performansını ölçmenizi ve darboğaz oluşturan satırları tanımlamanızı sağlar. Karmaşık projeler için, [ProfileView](https://github.com/timholy/ProfileView.jl) paketi profil sonuçlarınızı görselleştirmenize yardımcı olabilir.
  * [JET](https://github.com/aviatesk/JET.jl) paketi, kodunuzdaki yaygın performans sorunlarını bulmanıza yardımcı olabilir.
  * Beklenmedik şekilde büyük bellek tahsisleri – [`@time`](@ref), [`@allocated`](@ref) veya profil aracılığıyla (çöp toplama rutinlerine yapılan çağrılarla) bildirildiği gibi – kodunuzda sorun olabileceğine işaret eder. Tahsisler için başka bir neden görmüyorsanız, bir tür problemi olduğundan şüphelenin. Ayrıca, Julia'yı `--track-allocation=user` seçeneğiyle başlatabilir ve bu tahsislerin nerede gerçekleştiğine dair bilgileri görmek için oluşan `*.mem` dosyalarını inceleyebilirsiniz. [Memory allocation analysis](@ref)'ya bakın.
  * `@code_warntype` kodunuzun, tür belirsizliğine yol açan ifadeleri bulmanıza yardımcı olabilecek bir temsilini oluşturur. Aşağıda [`@code_warntype`](@ref)'yı görebilirsiniz.

## [Avoid containers with abstract type parameters](@id man-performance-abstract-container)

Parametreli türlerle, diziler de dahil olmak üzere çalışırken, mümkünse soyut türlerle parametre vermekten kaçınmak en iyisidir.

Aşağıdakileri dikkate alın:

```jldoctest
julia> a = Real[]
Real[]

julia> push!(a, 1); push!(a, 2.0); push!(a, π)
3-element Vector{Real}:
 1
 2.0
 π = 3.1415926535897...
```

Çünkü `a`, soyut türde bir dizi olan [`Real`](@ref) olduğundan, herhangi bir `Gerçek` değerini tutabilmelidir. `Gerçek` nesneleri keyfi boyut ve yapıda olabileceğinden, `a`'nın bireysel olarak tahsis edilmiş `Gerçek` nesnelerine işaret eden bir dizi olarak temsil edilmesi gerekir. Ancak, eğer `a`'da yalnızca aynı türde sayılara, örneğin [`Float64`](@ref), izin veriyorsak, bunlar daha verimli bir şekilde saklanabilir:

```jldoctest
julia> a = Float64[]
Float64[]

julia> push!(a, 1); push!(a, 2.0); push!(a,  π)
3-element Vector{Float64}:
 1.0
 2.0
 3.141592653589793
```

`a`'ya sayılar atamak artık bunları `Float64`'e dönüştürecek ve `a`, verimli bir şekilde işlenebilen 64-bit kayan nokta değerlerinin ardışık bir bloğu olarak saklanacaktır.

Eğer soyut değer türleriyle konteynerlerden kaçınamıyorsanız, bazen çalışma zamanı tür kontrolünden kaçınmak için `Any` ile parametre vermek daha iyidir. Örneğin, `IdDict{Any, Any}` `IdDict{Type, Vector}`'dan daha iyi performans gösterir.

Ayrıca [Parametric Types](@ref) altındaki tartışmaya bakın.

## Type declarations

Birçok dilde isteğe bağlı tür bildirimleri ile, bildirim eklemek kodun daha hızlı çalışmasını sağlamak için ana yoldur. Bu, Julia'da *böyle değildir*. Julia'da derleyici genellikle tüm fonksiyon argümanlarının, yerel değişkenlerin ve ifadelerin türlerini bilir. Ancak, bildirimlerin faydalı olduğu birkaç özel durum vardır.

### Avoid fields with abstract type

Alanlarının türlerini belirtmeden türler tanımlanabilir:

```jldoctest myambig
julia> struct MyAmbiguousType
           a
       end
```

Bu, `a`'nın herhangi bir türde olmasına izin verir. Bu genellikle faydalı olabilir, ancak bir dezavantajı vardır: `MyAmbiguousType` türündeki nesneler için derleyici yüksek performanslı kod üretemez. Bunun nedeni, derleyicinin nesnelerin değerlerini değil, türlerini kullanarak kodu nasıl oluşturacağını belirlemesidir. Ne yazık ki, `MyAmbiguousType` türündeki bir nesne hakkında çok az şey çıkarılabilir:

```jldoctest myambig
julia> b = MyAmbiguousType("Hello")
MyAmbiguousType("Hello")

julia> c = MyAmbiguousType(17)
MyAmbiguousType(17)

julia> typeof(b)
MyAmbiguousType

julia> typeof(c)
MyAmbiguousType
```

`b` ve `c` değerleri aynı türde olmasına rağmen, bellek içindeki veri temsilleri çok farklıdır. `a` alanında sadece sayısal değerler saklasanız bile, [`UInt8`](@ref)'nın bellek temsili ile [`Float64`](@ref)'nın bellek temsili arasındaki fark, CPU'nun bunları iki farklı türde talimatla işlemesi gerektiği anlamına gelir. Gerekli bilgiler türde mevcut olmadığından, bu tür kararlar çalışma zamanında alınmak zorundadır. Bu da performansı yavaşlatır.

`a`'n türünü belirtmekle daha iyi yapabilirsiniz. Burada, `a`'nın birkaç türden biri olabileceği duruma odaklanıyoruz; bu durumda doğal çözüm parametreleri kullanmaktır. Örneğin:

```jldoctest myambig2
julia> mutable struct MyType{T<:AbstractFloat}
           a::T
       end
```

Bu, daha iyi bir seçimdir.

```jldoctest myambig2
julia> mutable struct MyStillAmbiguousType
           a::AbstractFloat
       end
```

çünkü ilk sürüm, `a`'nın türünü sarıcı nesnenin türünden belirler. Örneğin:

```jldoctest myambig2
julia> m = MyType(3.2)
MyType{Float64}(3.2)

julia> t = MyStillAmbiguousType(3.2)
MyStillAmbiguousType(3.2)

julia> typeof(m)
MyType{Float64}

julia> typeof(t)
MyStillAmbiguousType
```

`a` alanının türü `m`'nin türünden kolayca belirlenebilir, ancak `t`'nin türünden belirlenemez. Gerçekten de, `t`'de `a` alanının türünü değiştirmek mümkündür:

```jldoctest myambig2
julia> typeof(t.a)
Float64

julia> t.a = 4.5f0
4.5f0

julia> typeof(t.a)
Float32
```

Buna karşın, `m` oluşturulduktan sonra `m.a`'nın tipi değiştirilemez:

```jldoctest myambig2
julia> m.a = 4.5f0
4.5f0

julia> typeof(m.a)
Float64
```

`m`'nin türünden `m.a`'nın türünün biliniyor olması - bununla birlikte, türünün işlev ortasında değişmeyeceği gerçeği - derleyicinin `m` gibi nesneler için yüksek derecede optimize edilmiş kod üretmesine, ancak `t` gibi nesneler için üretememesine olanak tanır.

Tabii ki, bunların hepsi yalnızca `m`'yi somut bir türle inşa edersek doğrudur. Bunu, onu soyut bir türle açıkça inşa ederek bozabiliriz:

```jldoctest myambig2
julia> m = MyType{AbstractFloat}(3.2)
MyType{AbstractFloat}(3.2)

julia> typeof(m.a)
Float64

julia> m.a = 4.5f0
4.5f0

julia> typeof(m.a)
Float32
```

Pratik amaçlar için, bu tür nesneler `MyStillAmbiguousType` nesneleriyle aynı şekilde davranır.

Basit bir fonksiyon için üretilen kod miktarını karşılaştırmak oldukça öğreticidir.

```julia
func(m::MyType) = m.a+1
```

kullanarak

```julia
code_llvm(func, Tuple{MyType{Float64}})
code_llvm(func, Tuple{MyType{AbstractFloat}})
```

Uzunluk nedenleriyle sonuçlar burada gösterilmemektedir, ancak bunu kendiniz denemek isteyebilirsiniz. İlk durumda tür tamamen belirtilmiş olduğundan, derleyicinin çalışma zamanında türü çözmek için herhangi bir kod üretmesine gerek yoktur. Bu, daha kısa ve daha hızlı kod ile sonuçlanır.

Birinin, tam olarak parametreleştirilmemiş türlerin soyut türler gibi davrandığını da aklında bulundurması gerekir. Örneğin, tam olarak belirtilmiş bir `Array{T,n}` somut olmasına rağmen, hiçbir parametre verilmeden `Array` kendisi somut değildir:

```jldoctest myambig3
julia> !isconcretetype(Array), !isabstracttype(Array), isstructtype(Array), !isconcretetype(Array{Int}), isconcretetype(Array{Int,1})
(true, true, true, true, true)
```

Bu durumda, `MyType`'i `a::Array` ile bir alan olarak tanımlamaktan kaçınmak ve bunun yerine alanı `a::Array{T,N}` veya `a::A` olarak tanımlamak daha iyi olur; burada `{T,N}` veya `A`, `MyType`'in parametreleridir.

Önceki tavsiye, bir yapının alanlarının işlevler veya daha genel olarak çağrılabilir nesneler olarak tasarlandığı durumlarda özellikle faydalıdır. Bir yapıyı aşağıdaki gibi tanımlamak çok caziptir:

```julia
struct MyCallableWrapper
    f::Function
end
```

Ama `Function` soyut bir tür olduğu için, `wrapper.f` çağrısının her biri, `f` alanına erişimin tür kararsızlığı nedeniyle dinamik yönlendirme gerektirecektir. Bunun yerine, şöyle bir şey yazmalısınız:

```julia
struct MyCallableWrapper{F}
    f::F
end
```

hangi neredeyse aynı davranışa sahip ancak çok daha hızlı olacaktır (çünkü tür belirsizliği ortadan kaldırılmıştır). `F<:Function` koşulunu koymadığımızı unutmayın: bu, `Function` alt türü olmayan çağrılabilir nesnelerin de `f` alanı için izin verildiği anlamına gelir.

### Avoid fields with abstract containers

Konteyner türleri için de aynı en iyi uygulamalar geçerlidir:

```jldoctest containers
julia> struct MySimpleContainer{A<:AbstractVector}
           a::A
       end

julia> struct MyAmbiguousContainer{T}
           a::AbstractVector{T}
       end

julia> struct MyAlsoAmbiguousContainer
           a::Array
       end
```

Örneğin:

```jldoctest containers
julia> c = MySimpleContainer(1:3);

julia> typeof(c)
MySimpleContainer{UnitRange{Int64}}

julia> c = MySimpleContainer([1:3;]);

julia> typeof(c)
MySimpleContainer{Vector{Int64}}

julia> b = MyAmbiguousContainer(1:3);

julia> typeof(b)
MyAmbiguousContainer{Int64}

julia> b = MyAmbiguousContainer([1:3;]);

julia> typeof(b)
MyAmbiguousContainer{Int64}

julia> d = MyAlsoAmbiguousContainer(1:3);

julia> typeof(d), typeof(d.a)
(MyAlsoAmbiguousContainer, Vector{Int64})

julia> d = MyAlsoAmbiguousContainer(1:1.0:3);

julia> typeof(d), typeof(d.a)
(MyAlsoAmbiguousContainer, Vector{Float64})

```

`MySimpleContainer` için, nesne türü ve parametreleri ile tamamen tanımlanmıştır, bu nedenle derleyici optimize edilmiş fonksiyonlar üretebilir. Çoğu durumda, bu muhtemelen yeterli olacaktır.

Derleyici artık işini mükemmel bir şekilde yapabiliyorken, `a`'nın *eleman türüne* bağlı olarak kodunuzun farklı şeyler yapmasını isteyebileceğiniz durumlar vardır. Genellikle bunu başarmanın en iyi yolu, belirli işleminizi (burada, `foo`) ayrı bir işlevin içine sarmaktır:

```jldoctest containers
julia> function sumfoo(c::MySimpleContainer)
           s = 0
           for x in c.a
               s += foo(x)
           end
           s
       end
sumfoo (generic function with 1 method)

julia> foo(x::Integer) = x
foo (generic function with 1 method)

julia> foo(x::AbstractFloat) = round(x)
foo (generic function with 2 methods)
```

Bu, her durumda derleyicinin optimize edilmiş kod üretmesine izin verirken işleri basit tutar.

Ancak, `MySimpleContainer` içindeki `a` alanının farklı eleman türleri veya `AbstractVector` türleri için dış işlevin farklı sürümlerini tanımlamanız gereken durumlar vardır. Bunu şu şekilde yapabilirsiniz:

```jldoctest containers
julia> function myfunc(c::MySimpleContainer{<:AbstractArray{<:Integer}})
           return c.a[1]+1
       end
myfunc (generic function with 1 method)

julia> function myfunc(c::MySimpleContainer{<:AbstractArray{<:AbstractFloat}})
           return c.a[1]+2
       end
myfunc (generic function with 2 methods)

julia> function myfunc(c::MySimpleContainer{Vector{T}}) where T <: Integer
           return c.a[1]+3
       end
myfunc (generic function with 3 methods)
```

```jldoctest containers
julia> myfunc(MySimpleContainer(1:3))
2

julia> myfunc(MySimpleContainer(1.0:3))
3.0

julia> myfunc(MySimpleContainer([1:3;]))
4
```

### Annotate values taken from untyped locations

Veri yapılarıyla çalışmak genellikle herhangi bir türde değerler içerebilen yapılarla ( `Array{Any}` türünde diziler) çalışmak için uygundur. Ancak, bu yapılardan birini kullanıyorsanız ve bir öğenin türünü biliyorsanız, bu bilgiyi derleyiciyle paylaşmak faydalıdır:

```julia
function foo(a::Array{Any,1})
    x = a[1]::Int32
    b = x+1
    ...
end
```

Burada, `a`'nın ilk elemanının [`Int32`](@ref) olacağını bilme şansımız oldu. Bu şekilde bir not eklemenin ek bir avantajı, eğer değer beklenen türde değilse bir çalışma zamanı hatası oluşturmasıdır, bu da belirli hataları daha erken yakalama potansiyeli taşır.

`a[1]` türü tam olarak bilinmediğinde, `x` şu şekilde tanımlanabilir: `x = convert(Int32, a[1])::Int32`. [`convert`](@ref) fonksiyonunun kullanımı, `a[1]`'in `Int32`'ye dönüştürülebilen herhangi bir nesne olmasına (örneğin `UInt8`) olanak tanır ve böylece kodun genel yapısını artırarak tür gereksinimini gevşetir. Bu bağlamda `convert`'in kendisinin tür istikrarını sağlamak için bir tür açıklamasına ihtiyaç duyduğunu unutmayın. Bunun nedeni, derleyicinin bir fonksiyonun dönüş değerinin türünü, hatta `convert`'in bile, fonksiyonun tüm argümanlarının türleri bilinmediği sürece çıkaramamış olmasıdır.

Tip anotasyonu, tür soyut olduğunda veya çalışma zamanında oluşturulduğunda performansı artırmayacak (ve aslında engelleyebilir). Bunun nedeni, derleyicinin anotasyonu kullanarak sonraki kodu özelleştirememesidir ve tür kontrolü kendisi zaman alır. Örneğin, kodda:

```julia
function nr(a, prec)
    ctype = prec == 32 ? Float32 : Float64
    b = Complex{ctype}(a)
    c = (b + 1.0f0)::Complex{ctype}
    abs(c)
end
```

`c` anotasyonu performansı olumsuz etkiler. Çalışma zamanında oluşturulan türlerle ilgili performanslı kod yazmak için aşağıda tartışılan [function-barrier technique](@ref kernel-functions)'i kullanın ve oluşturulan türün, çekirdek işlevinin argüman türleri arasında yer aldığından emin olun, böylece çekirdek işlemleri derleyici tarafından uygun şekilde özelleştirilir. Örneğin, yukarıdaki kod parçasında, `b` oluşturulduğu anda, başka bir işlev `k`'ye, çekirdek işlevine, geçirilebilir. Örneğin, `k` işlevi `b`'yi `Complex{T}` türünde bir argüman olarak tanımlıyorsa, burada `T` bir tür parametresidir, o zaman `k` içindeki bir atama ifadesinde aşağıdaki biçimde bir tür anotasyonu ortaya çıkar:

```julia
c = (b + 1.0f0)::Complex{T}
```

performansı engellemez (ama yardımcı da olmaz) çünkü derleyici `k` derlenirken `c`'nin türünü belirleyebilir.

### Be aware of when Julia avoids specializing

Bir sezgisel olarak, Julia `Type`, `Function` ve `Vararg` olmak üzere üç belirli durumda otomatik olarak [specializing](@ref man-method-specializations)'ı argüman tür parametrelerinde kullanmaktan kaçınır. Julia, argüman metod içinde kullanıldığında her zaman uzmanlaşır, ancak argüman başka bir işleve sadece iletildiğinde uzmanlaşmaz. Bu genellikle çalışma zamanında hiçbir performans etkisi yaratmaz ve [improves compiler performance](@ref compiler-efficiency-issues)'tadır. Eğer sizin durumunuzda çalışma zamanında bir performans etkisi olduğunu bulursanız, uzmanlaşmayı tetiklemek için yöntem bildirimine bir tür parametresi ekleyebilirsiniz. İşte bazı örnekler:

Bu, uzmanlaşmayacak:

```julia
function f_type(t)  # or t::Type
    x = ones(t, 10)
    return sum(map(sin, x))
end
```

ama bu şöyle olacak:

```julia
function g_type(t::Type{T}) where T
    x = ones(T, 10)
    return sum(map(sin, x))
end
```

Bunlar uzmanlaşmayacak:

```julia
f_func(f, num) = ntuple(f, div(num, 2))
g_func(g::Function, num) = ntuple(g, div(num, 2))
```

ama bu:

```julia
h_func(h::H, num) where {H} = ntuple(h, div(num, 2))
```

Bu, uzmanlaşmayacak:

```julia
f_vararg(x::Int...) = tuple(x...)
```

ama bu şöyle olacak:

```julia
g_vararg(x::Vararg{Int, N}) where {N} = tuple(x...)
```

Bir tek tür parametresi tanıtmak, diğer türler kısıtlanmamış olsa bile uzmanlaşmayı zorlamak için yeterlidir. Örneğin, bu da uzmanlaşacak ve argümanlar aynı türde olmadığında faydalıdır:

```julia
h_vararg(x::Vararg{Any, N}) where {N} = tuple(x...)
```

Not edin ki [`@code_typed`](@ref) ve arkadaşları her zaman size özel kod gösterecektir, Julia bu yöntem çağrısını normalde özelleştirmese bile. Argüman türleri değiştiğinde özelleştirmelerin üretilip üretilmediğini görmek istiyorsanız [method internals](@ref ast-lowered-method) kontrol etmelisiniz, yani `Base.specializations(@which f(...))` ifadesinin ilgili argüman için özelleştirmeleri içerip içermediğini kontrol etmelisiniz.

## Break functions into multiple definitions

Bir fonksiyonu birçok küçük tanım olarak yazmak, derleyicinin en uygun kodu doğrudan çağırmasına veya hatta iç içe almasına olanak tanır.

İşte gerçekten birden fazla tanım olarak yazılması gereken bir "bileşik fonksiyon" örneği:

```julia
using LinearAlgebra

function mynorm(A)
    if isa(A, Vector)
        return sqrt(real(dot(A,A)))
    elseif isa(A, Matrix)
        return maximum(svdvals(A))
    else
        error("mynorm: invalid argument")
    end
end
```

Bu daha özlü ve verimli bir şekilde şöyle yazılabilir:

```julia
mynorm(x::Vector) = sqrt(real(dot(x, x)))
mynorm(A::Matrix) = maximum(svdvals(A))
```

Ancak, derleyicinin `mynorm` örneği olarak yazılan koddaki ölü dalları optimize etmede oldukça verimli olduğu belirtilmelidir.

## Write "type-stable" functions

Bir işlevin her zaman aynı türde bir değer döndürmesini sağlamak mümkün olduğunda, bu faydalı olur. Aşağıdaki tanıma bakın:

```julia
pos(x) = x < 0 ? 0 : x
```

Bu masum görünüyor olsa da, sorun şu ki `0` bir tam sayıdır (tipi `Int`) ve `x` herhangi bir tipte olabilir. Dolayısıyla, `x`'in değerine bağlı olarak, bu fonksiyon iki farklı tipten bir değer döndürebilir. Bu davranış izin verilen bir durumdur ve bazı durumlarda istenebilir. Ancak, bu kolayca şu şekilde düzeltilebilir:

```julia
pos(x) = x < 0 ? zero(x) : x
```

Ayrıca [`oneunit`](@ref) fonksiyonu ve daha genel bir [`oftype(x, y)`](@ref) fonksiyonu bulunmaktadır; bu fonksiyon `y`'yi `x`'in türüne dönüştürür.

## Avoid changing the type of a variable

Bir benzer "tip-istikrarı" sorunu, bir fonksiyon içinde tekrar tekrar kullanılan değişkenler için mevcuttur:

```julia
function foo()
    x = 1
    for i = 1:10
        x /= rand()
    end
    return x
end
```

Yerel değişken `x` bir tamsayı olarak başlar ve bir döngü iterasyonundan sonra [`/`](@ref) operatörünün sonucu olarak bir kayan nokta sayısına dönüşür. Bu, derleyicinin döngü gövdesini optimize etmesini daha zor hale getirir. Birkaç olası çözüm vardır:

  * `x` ile `x = 1.0` olarak başlatın
  * `x::Float64 = 1`
  * `x = oneunit(Float64)` için açık bir dönüşüm kullanın.
  * İlk döngü yinelemesi ile başlatın, `x = 1 / rand()` olarak ayarlayın, ardından `for i = 2:10` döngüsünü başlatın.

## [Separate kernel functions (aka, function barriers)](@id kernel-functions)

Birçok fonksiyon, bir dizi hazırlık çalışması yapma ve ardından temel bir hesaplama gerçekleştirmek için birçok yineleme yapma desenini takip eder. Mümkünse, bu temel hesaplamaları ayrı fonksiyonlara koymak iyi bir fikirdir. Örneğin, aşağıdaki uydurma fonksiyon, rastgele seçilmiş bir türde bir dizi döndürür:

```jldoctest; setup = :(using Random; Random.seed!(1234))
julia> function strange_twos(n)
           a = Vector{rand(Bool) ? Int64 : Float64}(undef, n)
           for i = 1:n
               a[i] = 2
           end
           return a
       end;

julia> strange_twos(3)
3-element Vector{Int64}:
 2
 2
 2
```

Bu şöyle yazılmalıdır:

```jldoctest; setup = :(using Random; Random.seed!(1234))
julia> function fill_twos!(a)
           for i = eachindex(a)
               a[i] = 2
           end
       end;

julia> function strange_twos(n)
           a = Vector{rand(Bool) ? Int64 : Float64}(undef, n)
           fill_twos!(a)
           return a
       end;

julia> strange_twos(3)
3-element Vector{Int64}:
 2
 2
 2
```

Julia'nın derleyicisi, işlev sınırlarında argüman türleri için kodu özelleştirir, bu nedenle orijinal uygulamada döngü sırasında `a`'nın türünü bilmez (çünkü rastgele seçilir). Bu nedenle, ikinci versiyon genellikle daha hızlıdır çünkü iç döngü, `fill_twos!`'un farklı `a` türleri için yeniden derlenebilir.

İkinci form genellikle daha iyi bir stil olup daha fazla kod yeniden kullanımına yol açabilir.

Bu desen, Julia Base'te birkaç yerde kullanılmaktadır. Örneğin, `vcat` ve `hcat`'e bakın [`abstractarray.jl`](https://github.com/JuliaLang/julia/blob/40fe264f4ffaa29b749bcf42239a89abdcbba846/base/abstractarray.jl#L1205-L1206), veya kendi `fill_twos!` fonksiyonumuzu yazmak yerine kullanabileceğimiz [`fill!`](@ref) fonksiyonu.

`strange_twos` gibi işlevler, belirsiz türdeki verilerle çalışırken ortaya çıkar; örneğin, tam sayılar, ondalık sayılar, dizeler veya başka bir şey içerebilecek bir giriş dosyasından yüklenen veriler.

## [Types with values-as-parameters](@id man-performance-value-type)

`N` boyutlu ve her eksende 3 boyutuna sahip bir dizi oluşturmak istiyorsanız, bu dizileri şu şekilde oluşturabilirsiniz:

```jldoctest
julia> A = fill(5.0, (3, 3))
3×3 Matrix{Float64}:
 5.0  5.0  5.0
 5.0  5.0  5.0
 5.0  5.0  5.0
```

Bu yaklaşım çok iyi çalışıyor: derleyici, `A`'nın `Array{Float64,2}` olduğunu anlayabilir çünkü doldurma değerinin türünü (`5.0::Float64`) ve boyutunu (`(3, 3)::NTuple{2,Int}`) bilir. Bu, derleyicinin aynı işlevde `A`'nın gelecekteki herhangi bir kullanımına yönelik çok verimli kodlar üretebileceği anlamına gelir.

Ama şimdi, rastgele boyutlarda 3×3×... dizisi oluşturan bir fonksiyon yazmak istediğinizi varsayalım; bir fonksiyon yazma konusunda kendinizi zorlayabilirsiniz.

```jldoctest
julia> function array3(fillval, N)
           fill(fillval, ntuple(d->3, N))
       end
array3 (generic function with 1 method)

julia> array3(5.0, 2)
3×3 Matrix{Float64}:
 5.0  5.0  5.0
 5.0  5.0  5.0
 5.0  5.0  5.0
```

Bu çalışıyor, ancak (`@code_warntype array3(5.0, 2)` kullanarak kendiniz doğrulayabilirsiniz) sorun, çıktı türünün çıkarılamamasıdır: `N` argümanı bir `Int` türünde bir *değer*dir ve tür çıkarımı önceden değerini tahmin edemez (ve edemez). Bu, bu fonksiyonun çıktısını kullanan kodun temkinli olması gerektiği anlamına gelir; `A`'nın her erişiminde türü kontrol etmesi gerekir; böyle bir kod çok yavaş olacaktır.

Şimdi, bu tür sorunları çözmenin çok iyi bir yolu, [function-barrier technique](@ref kernel-functions) kullanmaktır. Ancak, bazı durumlarda tür kararsızlığını tamamen ortadan kaldırmak isteyebilirsiniz. Bu tür durumlarda, bir yaklaşım, boyutları bir parametre olarak geçmektir, örneğin `Val{T}()` aracılığıyla (bkz. ["Value types"](@ref)):

```jldoctest
julia> function array3(fillval, ::Val{N}) where N
           fill(fillval, ntuple(d->3, Val(N)))
       end
array3 (generic function with 1 method)

julia> array3(5.0, Val(2))
3×3 Matrix{Float64}:
 5.0  5.0  5.0
 5.0  5.0  5.0
 5.0  5.0  5.0
```

Julia, `ntuple`'ın ikinci parametre olarak bir `Val{::Int}` örneğini kabul eden özel bir versiyonuna sahiptir; `N`'yi bir tür parametresi olarak geçirerek, "değerini" derleyiciye bildirmiş olursunuz. Sonuç olarak, bu `array3` versiyonu derleyicinin dönüş türünü tahmin etmesine olanak tanır.

Ancak, bu tür tekniklerin kullanımı oldukça ince olabilir. Örneğin, `array3`'ü bu şekilde bir fonksiyondan çağırmanız faydalı olmayacaktır:

```julia
function call_array3(fillval, n)
    A = array3(fillval, Val(n))
end
```

Burada, aynı sorunu tekrar yaratmışsınız: derleyici `n`'in ne olduğunu tahmin edemez, bu yüzden `Val(n)`'in *tipini* bilemez. `Val`'ı kullanmaya çalışmak, ancak bunu yanlış bir şekilde yapmak, birçok durumda performansı *daha kötü* hale getirebilir. (Yalnızca `Val`'ı fonksiyon engeli hilesiyle birleştirerek çekirdek fonksiyonunu daha verimli hale getirmeye çalıştığınız durumlarda, yukarıdaki gibi bir kod kullanılmalıdır.)

Doğru kullanımına bir örnek `Val` şöyle olacaktır:

```julia
function filter3(A::AbstractArray{T,N}) where {T,N}
    kernel = array3(1, Val(N))
    filter(A, kernel)
end
```

Bu örnekte, `N` bir parametre olarak geçildiği için "değeri" derleyiciye bilinir. Temelde, `Val(T)` yalnızca `T` ya sabit/kodlanmış (`Val(3)`) ya da zaten tür alanında belirtilmiş olduğunda çalışır.

## The dangers of abusing multiple dispatch (aka, more on types with values-as-parameters)

Birisi çoklu dağıtımı takdir etmeyi öğrendiğinde, her şey için bunu kullanma eğilimi anlaşılabilir bir şekilde aşırıya kaçabilir. Örneğin, bilgileri depolamak için bunu kullanmayı hayal edebilirsiniz, örneğin:

```
struct Car{Make, Model}
    year::Int
    ...more fields...
end
```

ve sonra `Car{:Honda,:Accord}(year, args...)` gibi nesneler üzerinde dağıtım yapın.

Bu, aşağıdakilerden herhangi biri doğru olduğunda faydalı olabilir:

  * Her `Car` üzerinde CPU yoğun işlem gerektiriyorsanız ve `Make` ile `Model`'i derleme zamanında bilmek çok daha verimli hale geliyorsa, kullanılacak farklı `Make` veya `Model` sayısının çok büyük olmaması gerekir.
  * Homojen `Car` türünde listeleriniz var, böylece hepsini `Array{Car{:Honda,:Accord},N}` içinde depolayabilirsiniz.

Son durumda, böyle bir homojen diziyi işleyen bir fonksiyon verimli bir şekilde özelleştirilebilir: Julia, her bir elemanın türünü önceden bilir (konteynerdeki tüm nesneler aynı somut türe sahiptir), bu nedenle Julia, fonksiyon derlenirken doğru yöntem çağrılarını "arama" yapabilir (çalışma zamanında kontrol etme ihtiyacını ortadan kaldırarak) ve böylece tüm listeyi işlemek için verimli kod üretebilir.

Bu durumlar geçerli olmadığında, muhtemelen hiçbir fayda elde edemeyeceksiniz; daha kötüsü, ortaya çıkan "tiplerin kombinatoryal patlaması" ters etki yapacaktır. Eğer `items[i+1]` ile `item[i]` farklı bir tipe sahipse, Julia çalışma zamanında tipi kontrol etmek, uygun yöntemi yöntem tablolarında aramak, hangi yöntemin eşleştiğini (tip kesişimi aracılığıyla) belirlemek, henüz JIT derlenip derlenmediğini tespit etmek (eğer derlenmemişse bunu yapmak) ve ardından çağrıyı yapmak zorundadır. Özünde, tam tip sistemi ve JIT derleme mekanizmasını, kendi kodunuzda bir switch ifadesi veya sözlük araması gerçekleştirmesi için zorlamış oluyorsunuz.

Bazı çalışma zamanı karşılaştırmaları (1) tür dağıtımı, (2) sözlük araması ve (3) bir "switch" ifadesi ile ilgili olarak [on the mailing list](https://groups.google.com/forum/#!msg/julia-users/jUMu9A3QKQQ/qjgVWr7vAwAJ).

Belki de çalışma zamanı etkisinden daha kötü olan derleme zamanı etkisidir: Julia, her farklı `Car{Make, Model}` için özel işlevler derleyecektir; eğer yüzlerce veya binlerce böyle türünüz varsa, o zaman böyle bir nesneyi parametre olarak kabul eden her işlev (kendi yazabileceğiniz özel `get_year` işlevinden, Julia Temelindeki genel `push!` işlevine kadar) için yüzlerce veya binlerce varyant derlenecektir. Bunların her biri, derlenmiş kodun önbellek boyutunu, yöntemlerin iç listelerinin uzunluğunu vb. artırır. Değerleri parametre olarak kullanma konusundaki aşırı heves, kolayca muazzam kaynakları israf edebilir.

## [Access arrays in memory order, along columns](@id man-performance-column-major)

Julia'da çok boyutlu diziler sütun öncelikli sırada saklanır. Bu, dizilerin bir sütun bir seferde yığıldığı anlamına gelir. Bu, `vec` fonksiyonu veya aşağıda gösterildiği gibi `[:]` sözdizimi kullanılarak doğrulanabilir (dizinin `[1 3 2 4]` sırasına göre düzenlendiğini, `[1 2 3 4]` değil, dikkat edin):

```jldoctest
julia> x = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> x[:]
4-element Vector{Int64}:
 1
 3
 2
 4
```

Bu dizileri sıralama konvansiyonu, Fortran, Matlab ve R gibi birçok dilde yaygındır (birkaçını saymak gerekirse). Sütun-temelli sıralamanın alternatifi, C ve Python (`numpy`) gibi diğer dillerin benimsediği satır-temelli sıralamadır. Dizilerin sıralamasını hatırlamak, diziler üzerinde döngü kurarken önemli performans etkileri yaratabilir. Akılda tutulması gereken bir kural, sütun-temelli dizilerde ilk indeksin en hızlı değiştiğidir. Temelde bu, en içteki döngü indeksinin bir dilim ifadesinde ilk olarak görünmesi durumunda döngünün daha hızlı olacağı anlamına gelir. `:` ile bir diziyi indekslemenin, belirli bir boyuttaki tüm elemanlara iteratif olarak erişen örtük bir döngü olduğunu unutmayın; örneğin, sütunları çıkarmak satırlardan daha hızlı olabilir.

Aşağıdaki uydurma örneği düşünün. Bir [`Vector`](@ref) kabul eden ve kare bir [`Matrix`](@ref) döndüren bir fonksiyon yazmak istediğimizi hayal edin; bu kare, ya satırlar ya da sütunlar, girdi vektörünün kopyalarıyla doldurulmuş olsun. Bu kopyaların hangi şekilde doldurulduğunun önemli olmadığını varsayalım (belki de kodun geri kalanı buna göre kolayca uyarlanabilir). Bunu, yerleşik [`repeat`](@ref) çağrısına ek olarak en az dört farklı şekilde yapabiliriz:

```julia
function copy_cols(x::Vector{T}) where T
    inds = axes(x, 1)
    out = similar(Array{T}, inds, inds)
    for i = inds
        out[:, i] = x
    end
    return out
end

function copy_rows(x::Vector{T}) where T
    inds = axes(x, 1)
    out = similar(Array{T}, inds, inds)
    for i = inds
        out[i, :] = x
    end
    return out
end

function copy_col_row(x::Vector{T}) where T
    inds = axes(x, 1)
    out = similar(Array{T}, inds, inds)
    for col = inds, row = inds
        out[row, col] = x[row]
    end
    return out
end

function copy_row_col(x::Vector{T}) where T
    inds = axes(x, 1)
    out = similar(Array{T}, inds, inds)
    for row = inds, col = inds
        out[row, col] = x[col]
    end
    return out
end
```

Şimdi bu fonksiyonların her birini aynı rastgele `10000` x `1` girdi vektörü ile zamanlayacağız:

```julia-repl
julia> x = randn(10000);

julia> fmt(f) = println(rpad(string(f)*": ", 14, ' '), @elapsed f(x))

julia> map(fmt, [copy_cols, copy_rows, copy_col_row, copy_row_col]);
copy_cols:    0.331706323
copy_rows:    1.799009911
copy_col_row: 0.415630047
copy_row_col: 1.721531501
```

`copy_cols`'un `copy_rows`'dan çok daha hızlı olduğunu unutmayın. Bu beklenen bir durumdur çünkü `copy_cols`, `Matrix`'in sütun bazlı bellek düzenini dikkate alır ve her seferinde bir sütun doldurur. Ayrıca, `copy_col_row`, `copy_row_col`'dan çok daha hızlıdır çünkü dilim ifadesinde görünen ilk öğenin en içteki döngü ile birleştirilmesi gerektiği kuralımıza uyar.

## Pre-allocating outputs

Eğer fonksiyonunuz bir `Array` veya başka bir karmaşık tür döndürüyorsa, bellek ayırması gerekebilir. Ne yazık ki, genellikle bellek ayırma ve onun tersine, çöp toplama, önemli darboğazlar olabilir.

Bazen her fonksiyon çağrısında bellek ayırma ihtiyacını önceden ayırarak aşabilirsiniz. Basit bir örnek olarak, karşılaştırın

```jldoctest prealloc
julia> function xinc(x)
           return [x, x+1, x+2]
       end;

julia> function loopinc()
           y = 0
           for i = 1:10^7
               ret = xinc(i)
               y += ret[2]
           end
           return y
       end;
```

ile

```jldoctest prealloc
julia> function xinc!(ret::AbstractVector{T}, x::T) where T
           ret[1] = x
           ret[2] = x+1
           ret[3] = x+2
           nothing
       end;

julia> function loopinc_prealloc()
           ret = Vector{Int}(undef, 3)
           y = 0
           for i = 1:10^7
               xinc!(ret, i)
               y += ret[2]
           end
           return y
       end;
```

Zamanlama sonuçları:

```jldoctest prealloc; filter = r"[0-9\.]+ seconds \(.*?\)"
julia> @time loopinc()
  0.529894 seconds (40.00 M allocations: 1.490 GiB, 12.14% gc time)
50000015000000

julia> @time loopinc_prealloc()
  0.030850 seconds (6 allocations: 288 bytes)
50000015000000
```

Önceden tahsis etmenin başka avantajları da vardır; örneğin, çağıranın bir algoritmadan "çıktı" türünü kontrol etmesine olanak tanır. Yukarıdaki örnekte, isterseniz `SubArray` yerine [`Array`](@ref) geçirebilirdik.

Aşırıya kaçıldığında, ön tahsis kodunuzu çirkinleştirebilir, bu nedenle performans ölçümleri ve bazı yargılar gerekebilir. Ancak, "vektörleştirilmiş" (eleman bazında) fonksiyonlar için, geçici diziler olmadan birleştirilmiş döngülerle yerinde işlemler için `x .= f.(y)` kullanışlı sözdizimi kullanılabilir (bkz. [dot syntax for vectorizing functions](@ref man-vectorized)).

## [Use `MutableArithmetics` for more control over allocation for mutable arithmetic types](@id man-perftips-mutablearithmetics)

Bazı [`Number`](@ref) alt türleri, [`BigInt`](@ref) veya [`BigFloat`](@ref) gibi, [`mutable struct`](@ref) türleri olarak uygulanabilir veya değişken bileşenlere sahip olabilir. Julia `Base` içindeki aritmetik arayüzler genellikle bu tür durumlarda verimlilikten çok kullanım kolaylığını tercih eder, bu nedenle bunları naif bir şekilde kullanmak alt optimal performansa yol açabilir. Öte yandan, [`MutableArithmetics`](https://juliahub.com/ui/Packages/General/MutableArithmetics) paketinin soyutlamaları, bu türlerin değişkenliğinden yararlanarak yalnızca gerekli kadar bellek ayıran hızlı kod yazmayı mümkün kılar. `MutableArithmetics`, ayrıca gerektiğinde değişken aritmetik türlerinin değerlerini açıkça kopyalamayı da mümkün kılar. `MutableArithmetics`, bir kullanıcı paketidir ve Julia projesiyle bağlantılı değildir.

## More dots: Fuse vectorized operations

Julia, özel bir [dot syntax](@ref man-vectorized)'e sahiptir; bu, herhangi bir skalar fonksiyonu "vektörleştirilmiş" bir fonksiyon çağrısına ve herhangi bir operatörü "vektörleştirilmiş" bir operatöre dönüştürür. Özel bir özellik olarak, iç içe "nokta çağrıları" *birleştirilir*: bunlar, geçici diziler ayırmadan, sözdizimi düzeyinde tek bir döngüde birleştirilir. `.=` ve benzeri atama operatörlerini kullanırsanız, sonuç önceden tahsis edilmiş bir dizide yerinde de saklanabilir (yukarıya bakın).

Bir lineer cebir bağlamında, bu, `vector + vector` ve `vector * scalar` gibi işlemler tanımlı olsa da, bunun yerine `vector .+ vector` ve `vector .* scalar` kullanmanın avantajlı olabileceği anlamına gelir çünkü elde edilen döngüler çevresindeki hesaplamalarla birleştirilebilir. Örneğin, iki fonksiyonu düşünün:

```jldoctest dotfuse
julia> f(x) = 3x.^2 + 4x + 7x.^3;

julia> fdot(x) = @. 3x^2 + 4x + 7x^3; # equivalent to 3 .* x.^2 .+ 4 .* x .+ 7 .* x.^3
```

Her iki `f` ve `fdot` aynı şeyi hesaplar. Ancak, bir diziye uygulandığında `fdot` ( [`@.`](@ref @__dot__) makrosunun yardımıyla tanımlanmıştır) önemli ölçüde daha hızlıdır:

```jldoctest dotfuse; filter = r"[0-9\.]+ seconds \(.*?\)"
julia> x = rand(10^6);

julia> @time f(x);
  0.019049 seconds (16 allocations: 45.777 MiB, 18.59% gc time)

julia> @time fdot(x);
  0.002790 seconds (6 allocations: 7.630 MiB)

julia> @time f.(x);
  0.002626 seconds (8 allocations: 7.630 MiB)
```

Yani, `fdot(x)` on `f(x)`'in on katı hızında çalışır ve 1/6 oranında bellek ayırır, çünkü `f(x)`'teki her `*` ve `+` işlemi yeni bir geçici dizi ayırır ve ayrı bir döngüde çalışır. Bu örnekte `f.(x)` `fdot(x)` kadar hızlıdır, ancak birçok bağlamda, her vektörleştirilmiş işlem için ayrı bir fonksiyon tanımlamaktan ziyade ifadelerinize bazı noktalar eklemek daha kullanışlıdır.

## [Fewer dots: Unfuse certain intermediate broadcasts](@id man-performance-unfuse)

Yukarıda bahsedilen nokta döngü birleştirmesi, yüksek performanslı işlemleri ifade etmek için özlü ve deyimsel bir kod yazmayı sağlar. Ancak, birleştirilmiş işlemin her yayılma yinelemesinde hesaplanacağını unutmamak önemlidir. Bu, bazı durumlarda, özellikle bileşenli veya çok boyutlu yayılmaların varlığında, nokta çağrıları içeren bir ifadenin istenenden daha fazla kez bir fonksiyonu hesaplıyor olabileceği anlamına gelir. Örneğin, satırlarının Öklid normunun bir olduğu rastgele bir matris oluşturmak istiyoruz. Aşağıdaki gibi bir şey yazabiliriz:

```
julia> x = rand(1000, 1000);

julia> d = sum(abs2, x; dims=2);

julia> @time x ./= sqrt.(d);
  0.002049 seconds (4 allocations: 96 bytes)
```

Bu işe yarayacak. Ancak, bu ifade aslında `x[i, :]` satırındaki *her* eleman için `sqrt(d[i])`'yi yeniden hesaplayacak, bu da gerekli olandan çok daha fazla karekök hesaplandığı anlamına geliyor. Yayılmanın hangi indeksler üzerinde döneceğini tam olarak görmek için, birleşik ifadenin argümanları üzerinde `Broadcast.combine_axes` çağrısı yapabiliriz. Bu, döngü eksenlerine karşılık gelen aralıkların bir demetini döndürecektir; bu aralıkların uzunluklarının çarpımı, birleşik işlemin toplam çağrı sayısı olacaktır.

Bunun sonucunda, yayın ifadesinin bazı bileşenleri bir eksen boyunca sabit olduğunda—önceki örnekte olduğu gibi ikinci boyut boyunca `sqrt`—bu bileşenleri zorla "birleştirmeden ayırma" yoluyla performans iyileştirme potansiyeli vardır; yani, yayınlanan işlemin sonucunu önceden tahsis etmek ve sabit eksen boyunca önbelleğe alınan değeri yeniden kullanmaktır. Bu tür potansiyel yaklaşımlardan bazıları geçici değişkenler kullanmak, nokta ifadesinin bileşenlerini `identity` ile sarmak veya eşdeğer bir içsel vektörleştirilmiş (ancak birleştirilmemiş) fonksiyon kullanmaktır.

```
julia> @time let s = sqrt.(d); x ./= s end;
  0.000809 seconds (5 allocations: 8.031 KiB)

julia> @time x ./= identity(sqrt.(d));
  0.000608 seconds (5 allocations: 8.031 KiB)

julia> @time x ./= map(sqrt, d);
  0.000611 seconds (4 allocations: 8.016 KiB)
```

Bu seçeneklerden herhangi biri, bir tahsisat maliyetiyle yaklaşık üç kat hız artışı sağlar; büyük yayınlanabilirler için bu hız artışı asimptotik olarak çok büyük olabilir.

## [Consider using views for slices](@id man-performance-views)

Julia'da bir dizi "dilim" ifadesi olan `array[1:5, :]`, o verinin bir kopyasını oluşturur (atamanın sol tarafında `array[1:5, :] = ...` durumunda, o kısmına yerinde atama yapar). Eğer dilim üzerinde birçok işlem yapıyorsanız, bu performans için iyi olabilir çünkü daha küçük bir sürekli kopya ile çalışmak, orijinal diziye indekslemekten daha verimlidir. Öte yandan, eğer dilim üzerinde sadece birkaç basit işlem yapıyorsanız, tahsis ve kopyalama işlemlerinin maliyeti önemli olabilir.

Bir alternatif, dizinin bir "görünümünü" oluşturmaktır; bu, aslında orijinal dizinin verilerine yerinde referans veren bir dizi nesnesidir (bir `SubArray`), kopya oluşturmadan. (Bir görünümü yazarsanız, orijinal dizinin verilerini de değiştirir.) Bu, [`view`](@ref) çağrılarak bireysel dilimler için yapılabilir veya daha basit bir şekilde, o ifadenin önüne [`@views`](@ref) koyarak bir bütün ifade veya kod bloğu için yapılabilir. Örneğin:

```jldoctest; filter = r"[0-9\.]+ seconds \(.*?\)"
julia> fcopy(x) = sum(x[2:end-1]);

julia> @views fview(x) = sum(x[2:end-1]);

julia> x = rand(10^6);

julia> @time fcopy(x);
  0.003051 seconds (3 allocations: 7.629 MB)

julia> @time fview(x);
  0.001020 seconds (1 allocation: 16 bytes)
```

`fview` sürümünün işlevinin hem 3× hız artışını hem de azalan bellek tahsisini dikkate alın.

## Copying data is not always bad

Diziler, bellekte ardışık olarak saklanır ve bu da CPU vektörleştirmesine ve önbellek nedeniyle daha az bellek erişimine olanak tanır. Bu, dizilere sütun-birincil sırayla erişilmesi önerilen aynı nedenlerdir (yukarıya bakın). Düzensiz erişim desenleri ve ardışık olmayan görünümler, diziler üzerindeki hesaplamaları önemli ölçüde yavaşlatabilir çünkü ardışık olmayan bellek erişimi söz konusudur.

Düzensiz erişilen verileri tekrar erişimden önce bitişik bir diziye kopyalamak, aşağıdaki örnekte olduğu gibi büyük bir hız artışı sağlayabilir. Burada, bir matris rastgele karıştırılmış indekslerde erişilmektedir ve ardından çarpılmaktadır. Düz dizilere kopyalamak, kopyalama ve tahsisatın ek maliyetine rağmen çarpımı hızlandırır.

```julia-repl
julia> using Random

julia> A = randn(3000, 3000);

julia> x = randn(2000);

julia> inds = shuffle(1:3000)[1:2000];

julia> function iterated_neural_network(A, x, depth)
           for _ in 1:depth
               x .= max.(0, A * x)
           end
           argmax(x)
       end

julia> @time iterated_neural_network(view(A, inds, inds), x, 10)
  0.324903 seconds (12 allocations: 157.562 KiB)
1569

julia> @time iterated_neural_network(A[inds, inds], x, 10)
  0.054576 seconds (13 allocations: 30.671 MiB, 13.33% gc time)
1569
```

Yeterli bellek mevcutsa, görünümün bir diziye kopyalanmasının maliyeti, ardışık bir dizide tekrarlanan matris çarpımlarını yapmanın sağladığı hız artışıyla karşılanır.

## Consider StaticArrays.jl for small fixed-size vector/matrix operations

Eğer uygulamanız, sabit boyutlu (yani boyut yürütmeden önce biliniyor) birçok küçük (`< 100` eleman) dizi içeriyorsa, [StaticArrays.jl package](https://github.com/JuliaArrays/StaticArrays.jl) paketini kullanmayı düşünebilirsiniz. Bu paket, gereksiz yığın tahsisatlarını önleyen ve derleyicinin dizinin *boyutu* için kodu özelleştirmesine olanak tanıyan bir şekilde bu dizileri temsil etmenizi sağlar; örneğin, vektör işlemlerini tamamen açarak (döngüleri ortadan kaldırarak) ve elemanları CPU kayıtlarında saklayarak.

Örneğin, 2D geometrilerle hesaplamalar yapıyorsanız, 2 bileşenli vektörlerle birçok hesaplamanız olabilir. `StaticArrays.jl` kütüphanesinden `SVector` türünü kullanarak, `v` ve `w` vektörleri üzerinde `norm(3v - w)` gibi kullanışlı vektör notasyonu ve işlemleri kullanabilirsiniz; bu, derleyicinin kodu, `@inbounds hypot(3v[1]-w[1], 3v[2]-w[2])` ile eşdeğer minimal bir hesaplama için açmasına olanak tanır.

## Avoid string interpolation for I/O

Veri bir dosyaya (veya başka bir I/O cihazına) yazarken, ekstra ara dizgiler oluşturmak bir yük kaynağıdır. Bunun yerine:

```julia
println(file, "$a $b")
```

kullanmak:

```julia
println(file, a, " ", b)
```

Kodun ilk versiyonu bir dize oluşturur, ardından bunu dosyaya yazar, ikinci versiyon ise değerleri doğrudan dosyaya yazar. Ayrıca, bazı durumlarda dize interpolasyonunun okunmasının daha zor olabileceğini unutmayın. Dikkate alın:

```julia
println(file, "$(f(a))$(f(b))")
```

karşısında:

```julia
println(file, f(a), f(b))
```

## Optimize network I/O during parallel execution

Uzak bir işlevi paralel olarak yürütürken:

```julia
using Distributed

responses = Vector{Any}(undef, nworkers())
@sync begin
    for (idx, pid) in enumerate(workers())
        @async responses[idx] = remotecall_fetch(foo, pid, args...)
    end
end
```

daha hızlıdır:

```julia
using Distributed

refs = Vector{Any}(undef, nworkers())
for (idx, pid) in enumerate(workers())
    refs[idx] = @spawnat pid foo(args...)
end
responses = [fetch(r) for r in refs]
```

Eski sonuç, her işçi için tek bir ağ gidiş-dönüşüne yol açarken, diğeri iki ağ çağrısına neden olur - ilk olarak [`@spawnat`](@ref) tarafından ve ikincisi [`fetch`](@ref) nedeniyle (veya hatta [`wait`](@ref)). `4d61726b646f776e2e436f64652822222c202266657463682229_40726566`/`4d61726b646f776e2e436f64652822222c2022776169742229_40726566` de seri olarak yürütülmekte ve bu da genel olarak daha kötü bir performansa yol açmaktadır.

## Fix deprecation warnings

Bir kullanımdan kaldırılmış işlev, yalnızca bir kez ilgili bir uyarı yazdırmak için dahili olarak bir arama gerçekleştirir. Bu ek arama, önemli bir yavaşlamaya neden olabilir, bu nedenle kullanımdan kaldırılmış işlevlerin tüm kullanımları, uyarılarda önerildiği gibi değiştirilmelidir.

## Tweaks

Bunlar sıkı iç döngülerde yardımcı olabilecek bazı küçük noktalardır.

  * Gereksiz dizilerden kaçının. Örneğin, [`sum([x,y,z])`](@ref) yerine `x+y+z` kullanın.
  * [`abs2(z)`](@ref) yerine [`abs(z)^2`](@ref) kullanın. Genel olarak, karmaşık `z` için kodu [`abs2`](@ref) yerine [`abs`](@ref) kullanacak şekilde yeniden yazmaya çalışın.
  * Kullan [`div(x,y)`](@ref) tam sayılar için kesirli bölme yerine, [`trunc(x/y)`](@ref), [`fld(x,y)`](@ref) yerine [`floor(x/y)`](@ref) ve [`cld(x,y)`](@ref) yerine [`ceil(x/y)`](@ref).

## [Performance Annotations](@id man-performance-annotations)

Bazen belirli program özelliklerini vaat ederek daha iyi optimizasyonu etkinleştirebilirsiniz.

  * [`@inbounds`](@ref) dizisini ifadeler içinde dizi sınır kontrolünü ortadan kaldırmak için kullanın. Bunu yapmadan önce emin olun. Eğer alt dizinler sınırların dışındaysa, çökme veya sessiz bozulmalar yaşayabilirsiniz.
  * [`@fastmath`](@ref) kullanarak gerçek sayılar için doğru olan, ancak IEEE sayıları için farklılıklara yol açan kayan nokta optimizasyonlarına izin verin. Bunu yaparken dikkatli olun, çünkü bu sayısal sonuçları değiştirebilir. Bu, clang'ın `-ffast-math` seçeneğine karşılık gelir.
  * [`@simd`](@ref) for loops to promise that the iterations are independent and may be reordered.  Note that in many cases, Julia can automatically vectorize code without the `@simd` macro; it is only beneficial in cases where such a transformation would otherwise be illegal, including cases like allowing floating-point re-associativity and ignoring dependent memory accesses (`@simd ivdep`). Again, be very careful when asserting `@simd` as erroneously annotating a loop with dependent iterations may result in unexpected results. In particular, note that `setindex!` on some `AbstractArray` subtypes is inherently dependent upon iteration order. **This feature is experimental** and could change or disappear in future versions of Julia.

1:n kullanarak bir AbstractArray'ye indeksleme yapmak yaygın bir deyimdir, ancak Array alışılmadık indeksleme kullanıyorsa güvenli değildir ve sınır kontrolü kapatıldığında bir segmentasyon hatasına neden olabilir. Bunun yerine `LinearIndices(x)` veya `eachindex(x)` kullanın (ayrıca bkz. [Arrays with custom indices](@ref man-custom-indices)).

!!! note
    `@simd` en içteki `for` döngüsünün hemen önüne yerleştirilmesi gerekirken, hem `@inbounds` hem de `@fastmath` tekil ifadeler veya iç içe geçmiş kod bloklarında yer alan tüm ifadeler için uygulanabilir; örneğin, `@inbounds begin` veya `@inbounds for ...` kullanarak.


İşte hem `@inbounds` hem de `@simd` işaretlemesi ile bir örnek (burada, optimizasyoncunun çok zeki olmaya çalışmasını engellemek ve benchmark'ımızı boşa çıkarmamak için `@noinline` kullanıyoruz):

```julia
@noinline function inner(x, y)
    s = zero(eltype(x))
    for i=eachindex(x)
        @inbounds s += x[i]*y[i]
    end
    return s
end

@noinline function innersimd(x, y)
    s = zero(eltype(x))
    @simd for i = eachindex(x)
        @inbounds s += x[i] * y[i]
    end
    return s
end

function timeit(n, reps)
    x = rand(Float32, n)
    y = rand(Float32, n)
    s = zero(Float64)
    time = @elapsed for j in 1:reps
        s += inner(x, y)
    end
    println("GFlop/sec        = ", 2n*reps / time*1E-9)
    time = @elapsed for j in 1:reps
        s += innersimd(x, y)
    end
    println("GFlop/sec (SIMD) = ", 2n*reps / time*1E-9)
end

timeit(1000, 1000)
```

2.4GHz Intel Core i5 işlemcisine sahip bir bilgisayarda bu şunu üretir:

```
GFlop/sec        = 1.9467069505224963
GFlop/sec (SIMD) = 17.578554163920018
```

(`GFlop/sani` performansı ölçer ve daha büyük sayılar daha iyidir.)

İşte üç tür işaretlemenin bulunduğu bir örnek. Bu program önce bir boyutlu bir dizinin sonlu farkını hesaplar ve ardından sonucun L2-normunu değerlendirir:

```julia
function init!(u::Vector)
    n = length(u)
    dx = 1.0 / (n-1)
    @fastmath @inbounds @simd for i in 1:n #by asserting that `u` is a `Vector` we can assume it has 1-based indexing
        u[i] = sin(2pi*dx*i)
    end
end

function deriv!(u::Vector, du)
    n = length(u)
    dx = 1.0 / (n-1)
    @fastmath @inbounds du[1] = (u[2] - u[1]) / dx
    @fastmath @inbounds @simd for i in 2:n-1
        du[i] = (u[i+1] - u[i-1]) / (2*dx)
    end
    @fastmath @inbounds du[n] = (u[n] - u[n-1]) / dx
end

function mynorm(u::Vector)
    n = length(u)
    T = eltype(u)
    s = zero(T)
    @fastmath @inbounds @simd for i in 1:n
        s += u[i]^2
    end
    @fastmath @inbounds return sqrt(s)
end

function main()
    n = 2000
    u = Vector{Float64}(undef, n)
    init!(u)
    du = similar(u)

    deriv!(u, du)
    nu = mynorm(du)

    @time for i in 1:10^6
        deriv!(u, du)
        nu = mynorm(du)
    end

    println(nu)
end

main()
```

2.7 GHz Intel Core i7 işlemcisine sahip bir bilgisayarda bu şunu üretir:

```
$ julia wave.jl;
  1.207814709 seconds
4.443986180758249

$ julia --math-mode=ieee wave.jl;
  4.487083643 seconds
4.443986180758249
```

Burada, `--math-mode=ieee` seçeneği `@fastmath` makrosunu devre dışı bırakır, böylece sonuçları karşılaştırabiliriz.

Bu durumda, `@fastmath` nedeniyle hız artışı yaklaşık 3.7 katıdır. Bu alışılmadık derecede büyük – genel olarak, hız artışı daha küçük olacaktır. (Bu özel örnekte, benchmark'ın çalışma seti işlemcinin L1 önbelleğine sığacak kadar küçüktür, bu nedenle bellek erişim gecikmesi bir rol oynamaz ve hesaplama süresi CPU kullanımına bağlıdır. Birçok gerçek dünya programında bu durum böyle değildir.) Ayrıca, bu durumda bu optimizasyon sonucu değiştirmez – genel olarak, sonuç biraz farklı olacaktır. Bazı durumlarda, özellikle sayısal olarak kararsız algoritmalar için, sonuç çok farklı olabilir.

`@fastmath` anotasyonu, kayan nokta ifadelerini yeniden düzenler; örneğin, değerlendirme sırasını değiştirmek veya belirli özel durumların (inf, nan) meydana gelemeyeceğini varsaymak gibi. Bu durumda (ve bu özel bilgisayarda), `deriv` fonksiyonundaki `1 / (2*dx)` ifadesi döngüden çıkarılır (yani döngü dışında hesaplanır), sanki `idx = 1 / (2*dx)` yazmış gibi. Döngüde, `... / (2*dx)` ifadesi artık `... * idx` haline gelir ki bu da değerlendirmek için çok daha hızlıdır. Elbette, derleyici tarafından uygulanan gerçek optimizasyon ile elde edilen hız artışı, donanıma çok bağlıdır. Oluşturulan koddaki değişikliği incelemek için Julia'nın [`code_native`](@ref) fonksiyonunu kullanabilirsiniz.

`@fastmath` ayrıca hesaplama sırasında `NaN`'lerin meydana gelmeyeceğini varsayar, bu da şaşırtıcı davranışlara yol açabilir:

```julia-repl
julia> f(x) = isnan(x);

julia> f(NaN)
true

julia> f_fast(x) = @fastmath isnan(x);

julia> f_fast(NaN)
false
```

## Treat Subnormal Numbers as Zeros

Subnormal sayılar, daha önce [denormal numbers](https://en.wikipedia.org/wiki/Denormal_number) olarak adlandırılan, birçok bağlamda faydalıdır, ancak bazı donanımlarda performans cezası getirir. [`set_zero_subnormals(true)`](@ref) çağrısı, kayan nokta işlemlerinin subnormal giriş veya çıkışları sıfır olarak değerlendirmesine izin verir, bu da bazı donanımlarda performansı artırabilir. [`set_zero_subnormals(false)`](@ref) çağrısı, subnormal sayılar için katı IEEE davranışını zorlar.

Aşağıda, subnormal sayıların bazı donanımlarda performansı belirgin şekilde etkilediği bir örnek bulunmaktadır:

```julia
function timestep(b::Vector{T}, a::Vector{T}, Δt::T) where T
    @assert length(a)==length(b)
    n = length(b)
    b[1] = 1                            # Boundary condition
    for i=2:n-1
        b[i] = a[i] + (a[i-1] - T(2)*a[i] + a[i+1]) * Δt
    end
    b[n] = 0                            # Boundary condition
end

function heatflow(a::Vector{T}, nstep::Integer) where T
    b = similar(a)
    for t=1:div(nstep,2)                # Assume nstep is even
        timestep(b,a,T(0.1))
        timestep(a,b,T(0.1))
    end
end

heatflow(zeros(Float32,10),2)           # Force compilation
for trial=1:6
    a = zeros(Float32,1000)
    set_zero_subnormals(iseven(trial))  # Odd trials use strict IEEE arithmetic
    @time heatflow(a,1000)
end
```

Bu, aşağıdakine benzer bir çıktı verir

```
  0.002202 seconds (1 allocation: 4.063 KiB)
  0.001502 seconds (1 allocation: 4.063 KiB)
  0.002139 seconds (1 allocation: 4.063 KiB)
  0.001454 seconds (1 allocation: 4.063 KiB)
  0.002115 seconds (1 allocation: 4.063 KiB)
  0.001455 seconds (1 allocation: 4.063 KiB)
```

Her her bir çift yinelemenin önemli ölçüde daha hızlı olduğunu not edin.

Bu örnek, `a` içindeki değerlerin zamanla yavaşça düzleşen bir şekilde üssel olarak azalan bir eğri haline gelmesi nedeniyle birçok subnormal sayı üretir.

Subnormal sayıları sıfır olarak ele almak dikkatle kullanılmalıdır, çünkü bu bazı kimlikleri bozar, örneğin `x-y == 0` ifadesi `x == y` anlamına gelir:

```jldoctest
julia> x = 3f-38; y = 2f-38;

julia> set_zero_subnormals(true); (x - y, x == y)
(0.0f0, false)

julia> set_zero_subnormals(false); (x - y, x == y)
(1.0000001f-38, false)
```

Bazı uygulamalarda, alt normal sayıları sıfırlamanın bir alternatifi, küçük bir gürültü enjekte etmektir. Örneğin, `a`'yı sıfırlarla başlatmak yerine, onu şu şekilde başlatın:

```julia
a = rand(Float32,1000) * 1.f-9
```

## [[`@code_warntype`](@ref)](@id man-code-warntype)

Makro [`@code_warntype`](@ref) (veya işlev varyantı [`code_warntype`](@ref)) bazen türle ilgili sorunları teşhis etmede yardımcı olabilir. İşte bir örnek:

```julia-repl
julia> @noinline pos(x) = x < 0 ? 0 : x;

julia> function f(x)
           y = pos(x)
           return sin(y*x + 1)
       end;

julia> @code_warntype f(3.2)
MethodInstance for f(::Float64)
  from f(x) @ Main REPL[9]:1
Arguments
  #self#::Core.Const(f)
  x::Float64
Locals
  y::Union{Float64, Int64}
Body::Float64
1 ─      (y = Main.pos(x))
│   %2 = (y * x)::Float64
│   %3 = (%2 + 1)::Float64
│   %4 = Main.sin(%3)::Float64
└──      return %4
```

Interpreting the output of [`@code_warntype`](@ref), like that of its cousins [`@code_lowered`](@ref), [`@code_typed`](@ref), [`@code_llvm`](@ref), and [`@code_native`](@ref), takes a little practice. Your code is being presented in form that has been heavily digested on its way to generating compiled machine code. Most of the expressions are annotated by a type, indicated by the `::T` (where `T` might be [`Float64`](@ref), for example). The most important characteristic of [`@code_warntype`](@ref) is that non-concrete types are displayed in red; since this document is written in Markdown, which has no color, in this document, red text is denoted by uppercase.

En üstte, fonksiyonun çıkarılan dönüş türü `Body::Float64` olarak gösterilmektedir. Sonraki satırlar, `f`'nin Julia'nın SSA IR formundaki gövdesini temsil etmektedir. Numara verilmiş kutular etiketlerdir ve kodunuzdaki atlamalar ( `goto` aracılığıyla) için hedefleri temsil eder. Gövdeye baktığınızda, ilk olarak `pos` çağrıldığını ve dönüş değerinin büyük harfle gösterilen `Union` türü `Union{Float64, Int64}` olarak çıkarıldığını görebilirsiniz, çünkü bu bir somut olmayan türdür. Bu, `pos`'un dönüş türünü girdi türlerine dayanarak kesin olarak bilemeyeceğimiz anlamına gelir. Ancak, `y*x` sonucunun, `y` bir `Float64` veya `Int64` olsa da her durumda bir `Float64` olduğu gerçeği vardır. Sonuç olarak, `f(x::Float64)` çıktısında tür açısından dengesiz olmayacaktır, bazı ara hesaplamalar tür açısından dengesiz olsa bile.

Bu bilgiyi nasıl kullanacağınız size kalmış. Açıkça, `pos`'u tür açısından kararlı hale getirmek en iyi seçenek olacaktır: eğer bunu yaparsanız, `f` içindeki tüm değişkenler somut hale gelir ve performansı optimal olur. Ancak, bu tür *geçici* tür kararsızlığının çok da önemli olmadığı durumlar vardır: örneğin, `pos` hiçbir zaman yalnız kullanılmıyorsa, `f`'nin çıktısının tür açısından kararlı olması (örneğin, [`Float64`](@ref) girdileri için) sonraki kodu tür kararsızlığının yayılma etkilerinden koruyacaktır. Bu, tür kararsızlığını düzeltmenin zor veya imkansız olduğu durumlarda özellikle önemlidir. Bu tür durumlarda, yukarıdaki ipuçları (örneğin, tür açıklamaları eklemek ve/veya fonksiyonları bölmek) tür kararsızlığından kaynaklanan "zararı" sınırlamak için en iyi araçlarınızdır. Ayrıca, Julia Base'in bile tür açısından kararsız olan fonksiyonları olduğunu unutmayın. Örneğin, [`findfirst`](@ref) fonksiyonu bir anahtarın bulunduğu bir dizideki indeksi döndürür veya bulunamazsa `nothing` döndürür; bu, belirgin bir tür kararsızlığıdır. Önemli olabilecek tür kararsızlıklarını bulmayı kolaylaştırmak için, `missing` veya `nothing` içeren `Union`'lar sarı renkle vurgulanmıştır, kırmızı yerine.

Aşağıdaki örnekler, yaprak olmayan türler içerdiği belirtilen ifadeleri yorumlamanıza yardımcı olabilir:

  * Fonksiyon gövdesi `Body::Union{T1,T2})` ile başlıyor.

      * Yorumlama: kararsız dönüş türüne sahip fonksiyon
      * Öneri: dönen değer tür açısından kararlı hale getirin, gerekirse onu anotlayın.
  * `invoke Main.g(%%x::Int64)::Union{Float64, Int64}`

      * Yorum: tür-istikrarsız bir fonksiyon `g` çağrısı.
      * Öneri: fonksiyonu düzeltin veya gerekirse dönüş değerini açıklayın
  * `Base.getindex(%%x::Array{Any,1}, 1::Int64)::Any`

      * Yorumlama: kötü tipli dizilerin elemanlarına erişim
      * Öneri: Daha iyi tanımlanmış türlerle diziler kullanın veya gerekirse bireysel eleman erişimlerinin türünü anotlayın.
  * `Base.getfield(%%x, :(:data))::Array{Float64,N} where N`

      * Yorum: yaprak olmayan türde bir alan almak. Bu durumda, `x`'in türü, diyelim ki `ArrayContainer`, `data::Array{T}` alanına sahipti. Ancak `Array`, somut bir tür olabilmesi için boyut `N`'ye de ihtiyaç duyar.
      * Öneri: `Array{T,3}` veya `Array{T,N}` gibi somut türler kullanın; burada `N`, artık `ArrayContainer`'ın bir parametresidir.

## [Performance of captured variable](@id man-performance-captured)

Aşağıdaki iç fonksiyonu tanımlayan örneği dikkate alın:

```julia
function abmult(r::Int)
    if r < 0
        r = -r
    end
    f = x -> x * r
    return f
end
```

Fonksiyon `abmult`, `r`'nin mutlak değeri ile argümanını çarpan bir `f` fonksiyonu döndürür. `f`'ye atanan iç fonksiyona "closure" denir. İç fonksiyonlar, dil tarafından `do` blokları ve jeneratör ifadeleri için de kullanılır.

Bu kod stili, dil için performans zorlukları sunar. Ayrıştırıcı, bunu daha düşük seviyeli talimatlara çevirirken, yukarıdaki kodu önemli ölçüde yeniden düzenleyerek iç işlevi ayrı bir kod bloğuna çıkarır. İç işlevler ve onları saran kapsam tarafından paylaşılan "yakalanmış" değişkenler, `r` gibi, hem iç hem de dış işlevlere erişilebilen yığın tahsisli bir "kutucuğa" da çıkarılır çünkü dil, iç kapsamda `r`'nin dış kapsamda `r` ile aynı olması gerektiğini belirtir; bu, dış kapsam (veya başka bir iç işlev) `r`'yi değiştirdikten sonra bile geçerlidir.

Önceki paragraftaki tartışma "parsing" ile ilgiliydi, yani `abmult` içeren modülün ilk yüklendiği sırada gerçekleşen derleme aşaması, ilk kez çağrıldığı sonraki aşamaya karşı. Parser, `Int`'in sabit bir tür olduğunu veya `r = -r` ifadesinin bir `Int`'i başka bir `Int`'ye dönüştürdüğünü "bilmez". Tür çıkarımının sihri, derlemenin sonraki aşamasında gerçekleşir.

Böylece, ayrıştırıcı `r`'nin sabit bir türü (`Int`) olduğunu bilmez. Ayrıca, iç fonksiyon oluşturulduktan sonra `r`'nin değerinin değişmeyeceğini de bilmez (bu nedenle kutuya ihtiyaç yoktur). Bu nedenle, ayrıştırıcı, `r`'nin her bir kullanımında çalışma zamanı türü dağıtımı gerektiren `Any` gibi soyut bir türü tutan bir kutu için kod üretir. Bu, yukarıdaki fonksiyona `@code_warntype` uygulayarak doğrulanabilir. Hem kutulama hem de çalışma zamanı türü dağıtımı performans kaybına neden olabilir.

Eğer yakalanan değişkenler kodun performans açısından kritik bir bölümünde kullanılıyorsa, o zaman bu değişkenlerin performansını artırmak için aşağıdaki ipuçları yardımcı olur. İlk olarak, yakalanan bir değişkenin türünün değişmeyeceği biliniyorsa, bu açıkça bir tür açıklaması ile belirtilebilir (değişken üzerinde, sağ taraf üzerinde değil):

```julia
function abmult2(r0::Int)
    r::Int = r0
    if r < 0
        r = -r
    end
    f = x -> x * r
    return f
end
```

Tip anotasyonu, kutudaki nesneye somut bir tür ilişkilendirebildiği için yakalanma nedeniyle kaybolan performansı kısmen geri kazandırır. Daha da ileri giderek, eğer yakalanan değişkenin (kapanış oluşturulduktan sonra yeniden atanmayacağı için) hiç kutulanmasına gerek yoksa, bu `let` blokları ile aşağıdaki gibi belirtilebilir.

```julia
function abmult3(r::Int)
    if r < 0
        r = -r
    end
    f = let r = r
            x -> x * r
    end
    return f
end
```

`let` bloğu, yalnızca iç işlevin kapsamına sahip yeni bir `r` değişkeni oluşturur. İkinci teknik, yakalanmış değişkenlerin varlığında tam dil performansını geri kazandırır. Bunun, derleyicinin hızla gelişen bir yönü olduğunu ve gelecekteki sürümlerin bu düzeyde programcı notasyonu gerektirmeyeceğini belirtmek önemlidir. Bu arada, [FastClosures](https://github.com/c42f/FastClosures.jl) gibi bazı kullanıcı katkılı paketler, `abmult3`'te olduğu gibi `let` ifadelerinin eklenmesini otomatikleştirir.

## [Multithreading and linear algebra](@id man-multithreading-linear-algebra)

Bu bölüm, her bir iş parçacığında lineer cebir işlemleri gerçekleştiren çok iş parçacıklı Julia koduna uygulanır. Gerçekten de, bu lineer cebir işlemleri, kendileri de çok iş parçacıklı olan BLAS / LAPACK çağrılarını içerir. Bu durumda, iki farklı çok iş parçacıklı tür nedeniyle çekirdeklerin aşırı abone olmamasını sağlamak gerekir.

Julia, lineer cebir için kendi OpenBLAS kopyasını derler ve kullanır; bu kopyanın iş parçacığı sayısı `OPENBLAS_NUM_THREADS` ortam değişkeni ile kontrol edilir. Bu, Julia'yı başlatırken bir komut satırı seçeneği olarak ayarlanabilir veya Julia oturumu sırasında `BLAS.set_num_threads(N)` ile değiştirilebilir (alt modül `BLAS`, `using LinearAlgebra` ile dışa aktarılır). Mevcut değeri `BLAS.get_num_threads()` ile erişilebilir.

Kullanıcı hiçbir şey belirtmediğinde, Julia, OpenBLAS iş parçacıklarının sayısı için makul bir değer seçmeye çalışır (örneğin, platforma, Julia sürümüne vb. dayanarak). Ancak, değeri manuel olarak kontrol etmek ve ayarlamak genellikle önerilir. OpenBLAS davranışı şu şekildedir:

  * Eğer `OPENBLAS_NUM_THREADS=1` ise, OpenBLAS çağıran Julia iş parçacığını(larını) kullanır, yani hesaplamayı yürüten Julia iş parçacığında "yaşar".
  * Eğer `OPENBLAS_NUM_THREADS=N>1` ise, OpenBLAS kendi thread havuzunu oluşturur ve yönetir (`N` toplamda). Tüm Julia thread'leri arasında paylaşılan sadece bir OpenBLAS thread havuzu vardır.

Julia'yı çok iş parçacıklı modda `JULIA_NUM_THREADS=X` ile başlattığınızda, genellikle `OPENBLAS_NUM_THREADS=1` olarak ayarlamanız önerilir. Yukarıda açıklanan davranış göz önüne alındığında, BLAS iş parçacıklarının sayısını `N>1` olarak artırmak, özellikle `N<<X` olduğunda, çok kolay bir şekilde daha kötü performansa yol açabilir. Ancak bu sadece bir kuraldır ve her bir iş parçacığı sayısını ayarlamanın en iyi yolu, belirli uygulamanızda denemeler yapmaktır.

## [Alternative linear algebra backends](@id man-backends-linear-algebra)

OpenBLAS'a alternatif olarak, lineer cebir performansına yardımcı olabilecek birkaç başka arka uç bulunmaktadır. Öne çıkan örnekler arasında [MKL.jl](https://github.com/JuliaLinearAlgebra/MKL.jl) ve [AppleAccelerate.jl](https://github.com/JuliaMath/AppleAccelerate.jl) bulunmaktadır.

Bunlar harici paketlerdir, bu nedenle burada ayrıntılı olarak tartışmayacağız. Lütfen ilgili belgelerine başvurun (özellikle çok iş parçacıklı çalışma ile ilgili olarak OpenBLAS'tan farklı davranışları olduğu için).

## Execution latency, package loading and package precompiling time

### Reducing time to first plot etc.

İlk kez bir julia yöntemi çağrıldığında, bu yöntem (ve çağırdığı herhangi bir yöntem veya statik olarak belirlenebilenler) derlenecektir. [`@time`](@ref) makro ailesi bunu göstermektedir.

```
julia> foo() = rand(2,2) * rand(2,2)
foo (generic function with 1 method)

julia> @time @eval foo();
  0.252395 seconds (1.12 M allocations: 56.178 MiB, 2.93% gc time, 98.12% compilation time)

julia> @time @eval foo();
  0.000156 seconds (63 allocations: 2.453 KiB)
```

`@time @eval` derlemenin süresini ölçmek için daha iyidir çünkü [`@eval`](@ref) olmadan, bazı derlemeler zamanlamanın başlamasından önce yapılmış olabilir.

Bir paket geliştirirken, kullanıcılarınızın deneyimini *ön derleme* ile iyileştirebilirsiniz, böylece paketlerini kullandıklarında kullandıkları kod zaten derlenmiş olur. Paket kodunu etkili bir şekilde ön derlemek için, tipik paket kullanımını temsil eden bir "ön derleme iş yükü" çalıştırmak üzere [`PrecompileTools.jl`](https://julialang.github.io/PrecompileTools.jl/stable/) kullanmanız önerilir. Bu, yerel derlenmiş kodu paket `pkgimage` önbelleğine kaydedecek ve bu tür kullanım için "ilk yürütme süresini" (genellikle TTFX olarak adlandırılır) büyük ölçüde azaltacaktır.

Not edin ki [`PrecompileTools.jl`](https://julialang.github.io/PrecompileTools.jl/stable/) iş yükleri devre dışı bırakılabilir ve bazen önceden derleme yapmak istemiyorsanız Tercihler aracılığıyla yapılandırılabilir; bu, bir paketin geliştirilmesi sırasında geçerli olabilir.

### Reducing package loading time

Paketin yüklenme süresini düşük tutmak genellikle faydalıdır. Paket geliştiricileri için genel iyi uygulamalar şunları içerir:

1. Bağlılıklarınızı gerçekten ihtiyaç duyduğunuzlarla sınırlayın. Temel bağımlılıklarınızı şişirmeden diğer paketlerle birlikte çalışabilirliği desteklemek için [package extensions](@ref) kullanmayı düşünün.
2. [`__init__()`](@ref) fonksiyonlarının alternatif yoksa kullanılmasından kaçının, özellikle çok fazla derleme tetikleyebilecek veya uzun süre çalışması gerekenler.
3. Mümkünse, bağımlılıklarınızdan ve paket kodunuzdan [invalidations](https://julialang.org/blog/2020/08/invalidations/)'yi düzeltin.

[`@time_imports`](@ref) aracı, yukarıdaki faktörleri gözden geçirmek için REPL'de faydalı olabilir.

```julia-repl
julia> @time @time_imports using Plots
      0.5 ms  Printf
     16.4 ms  Dates
      0.7 ms  Statistics
               ┌ 23.8 ms SuiteSparse_jll.__init__() 86.11% compilation time (100% recompilation)
     90.1 ms  SuiteSparse_jll 91.57% compilation time (82% recompilation)
      0.9 ms  Serialization
               ┌ 39.8 ms SparseArrays.CHOLMOD.__init__() 99.47% compilation time (100% recompilation)
    166.9 ms  SparseArrays 23.74% compilation time (100% recompilation)
      0.4 ms  Statistics → SparseArraysExt
      0.5 ms  TOML
      8.0 ms  Preferences
      0.3 ms  PrecompileTools
      0.2 ms  Reexport
... many deps omitted for example ...
      1.4 ms  Tar
               ┌ 73.8 ms p7zip_jll.__init__() 99.93% compilation time (100% recompilation)
     79.4 ms  p7zip_jll 92.91% compilation time (100% recompilation)
               ┌ 27.7 ms GR.GRPreferences.__init__() 99.77% compilation time (100% recompilation)
     43.0 ms  GR 64.26% compilation time (100% recompilation)
               ┌ 2.1 ms Plots.__init__() 91.80% compilation time (100% recompilation)
    300.9 ms  Plots 0.65% compilation time (100% recompilation)
  1.795602 seconds (3.33 M allocations: 190.153 MiB, 7.91% gc time, 39.45% compilation time: 97% of which was recompilation)

```

Bu örnekte birden fazla paket yüklendiğine dikkat edin, bazıları `__init__()` fonksiyonlarına sahip, bazıları ise derleme yapar, bunların bir kısmı yeniden derleme yapar. Yeniden derleme, önceki paketlerin yöntemleri geçersiz kılmasıyla oluşur; bu durumlarda, takip eden paketler `__init__()` fonksiyonlarını çalıştırdıklarında, kod çalıştırılmadan önce bazıları yeniden derleme ile karşılaşır.

Ayrıca, `SparseArrays` bağımlılık ağacında bulunduğu için `Statistics` uzantısı `SparseArraysExt` etkinleştirilmiştir. Yani, `0.4 ms  Statistics → SparseArraysExt` kısmına bakın.

Bu rapor, bağımlılık yükleme süresinin maliyetinin getirdiği işlevselliğe değip değmediğini gözden geçirmek için iyi bir fırsat sunuyor. Ayrıca `Pkg` yardımcı programı `why`, dolaylı bir bağımlılığın neden var olduğunu raporlamak için kullanılabilir.

```
(CustomPackage) pkg> why FFMPEG_jll
  Plots → FFMPEG → FFMPEG_jll
  Plots → GR → GR_jll → FFMPEG_jll
```

veya bir paketin getirdiği dolaylı bağımlılıkları görmek için, paketi `pkg> rm` ile kaldırabilir, manifestodan kaldırılan bağımlılıkları görebilir ve ardından değişikliği `pkg> undo` ile geri alabilirsiniz.

Eğer yükleme süresi, derleme içeren yavaş `__init__()` yöntemleri tarafından belirleniyorsa, derlenenlerin ne olduğunu belirlemenin bir yolu, `--trace-compile=stderr` julia argümanını kullanmaktır. Bu, her derlendiğinde [`precompile`](@ref) ifadesini raporlayacaktır. Örneğin, tam kurulum şöyle olacaktır:

```
$ julia --startup-file=no --trace-compile=stderr
julia> @time @time_imports using CustomPackage
...
```

`--startup-file=no` ifadesine dikkat edin, bu, testi `startup.jl` dosyanızda bulunan paketlerden izole etmeye yardımcı olur.

Daha fazla yeniden derleme nedenlerinin analizi, [`SnoopCompile`](https://github.com/timholy/SnoopCompile.jl) paketini kullanarak gerçekleştirilebilir.
