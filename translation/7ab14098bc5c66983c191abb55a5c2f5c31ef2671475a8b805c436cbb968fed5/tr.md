# Style Guide

Aşağıdaki bölümler, idiyomatik Julia kodlama stilinin birkaç yönünü açıklamaktadır. Bu kuralların hiçbiri mutlak değildir; bunlar yalnızca dili tanımanıza ve alternatif tasarımlar arasında seçim yapmanıza yardımcı olmak için önerilerdir.

## Indentation

Tamam, 4 boşluk kullanarak girintileme seviyesini uygulayacağım.

## Write functions, not just scripts

Kod yazmak, bir problemi çözmeye başlamak için üst düzeyde bir dizi adım olarak hızlı bir yoldur, ancak bir programı mümkün olan en kısa sürede fonksiyonlara ayırmaya çalışmalısınız. Fonksiyonlar daha yeniden kullanılabilir ve test edilebilir, ayrıca hangi adımların yapıldığını ve bunların girdileri ile çıktılarının ne olduğunu netleştirir. Dahası, fonksiyonlar içindeki kod, Julia'nın derleyicisinin çalışma şekli nedeniyle üst düzey koddan çok daha hızlı çalışma eğilimindedir.

Ayrıca, fonksiyonların doğrudan küresel değişkenler üzerinde işlem yapmak yerine argüman alması gerektiğini vurgulamak da önemlidir (sabitler gibi [`pi`](@ref) hariç).

## Avoid writing overly-specific types

Kod, mümkün olduğunca genel olmalıdır. Şu şekilde yazmak yerine:

```julia
Complex{Float64}(x)
```

mevcut genel işlevleri kullanmak daha iyidir:

```julia
complex(float(x))
```

İkinci versiyon, `x`'i her zaman aynı türde yerine uygun bir türe dönüştürecektir.

Bu stil noktası, özellikle işlev argümanları için geçerlidir. Örneğin, gerçekten herhangi bir tam sayı olabileceği durumlarda bir argümanı `Int` veya [`Int32`](@ref) türünde tanımlamayın, bunun yerine soyut tür [`Integer`](@ref) ile ifade edin. Aslında, birçok durumda, diğer yöntem tanımlarından ayırt etmek için gerekli olmadıkça argüman türünü tamamen atlayabilirsiniz, çünkü bir tür, gerekli işlemlerden herhangi birini desteklemiyorsa, yine de bir [`MethodError`](@ref) fırlatılacaktır. (Bu, [duck typing](https://en.wikipedia.org/wiki/Duck_typing) olarak bilinir.)

Örneğin, bir argümanına bir ekleyen `addone` fonksiyonunun aşağıdaki tanımlarını düşünün:

```julia
addone(x::Int) = x + 1                 # works only for Int
addone(x::Integer) = x + oneunit(x)    # any integer type
addone(x::Number) = x + oneunit(x)     # any numeric type
addone(x) = x + oneunit(x)             # any type supporting + and oneunit
```

Son tanım `addone`, [`oneunit`](@ref) (bu, `x` ile aynı türde 1 döndürür, istenmeyen tür yükseltmesini önler) ve bu argümanlarla [`+`](@ref) fonksiyonunu işler. Fark edilmesi gereken ana şey, *yalnızca* genel `addone(x) = x + oneunit(x)` tanımının yapılmasının *hiçbir performans cezası* getirmediğidir, çünkü Julia otomatik olarak gerektiğinde özel sürümler derleyecektir. Örneğin, `addone(12)` çağrısını ilk yaptığınızda, Julia otomatik olarak `x::Int` argümanları için özel bir `addone` fonksiyonu derleyecek ve `oneunit` çağrısını, iç içe geçmiş değeri `1` ile değiştirecektir. Bu nedenle, yukarıdaki `addone`'ın ilk üç tanımı, dördüncü tanımla tamamen gereksizdir.

## Handle excess argument diversity in the caller

Bunun yerine:

```julia
function foo(x, y)
    x = Int(x); y = Int(y)
    ...
end
foo(x, y)
```

kullanmak:

```julia
function foo(x::Int, y::Int)
    ...
end
foo(Int(x), Int(y))
```

Bu daha iyi bir stil çünkü `foo` gerçekten her türden sayıları kabul etmiyor; aslında `Int`'lere ihtiyacı var.

Bir sorun, bir fonksiyonun doğası gereği tam sayılar gerektirmesi durumunda, çağıranın ondalık sayıların nasıl dönüştürüleceğine (örneğin, aşağı yuvarlama veya yukarı yuvarlama) karar vermesini zorlamak olabileceğidir. Diğer bir sorun ise, daha spesifik türlerin tanımlanmasının gelecekteki yöntem tanımları için daha fazla "alan" bırakmasıdır.

## [Append `!` to names of functions that modify their arguments](@id bang-convention)

Bunun yerine:

```julia
function double(a::AbstractArray{<:Number})
    for i in eachindex(a)
        a[i] *= 2
    end
    return a
end
```

kullanmak:

```julia
function double!(a::AbstractArray{<:Number})
    for i in eachindex(a)
        a[i] *= 2
    end
    return a
end
```

Julia Temel, bu konvansiyonu her yerde kullanır ve hem kopyalama hem de değiştirme biçimlerine sahip fonksiyonların örneklerini içerir (örneğin, [`sort`](@ref) ve [`sort!`](@ref)), ve sadece değiştiren diğerleri (örneğin, [`push!`](@ref), [`pop!`](@ref), [`splice!`](@ref)). Bu tür fonksiyonların genellikle, kullanım kolaylığı için değiştirilmiş diziyi de döndürmesi tipiktir.

IO veya rastgele sayı üreteçleri (RNG) ile ilgili işlevler, dikkate değer istisnalardır: Bu işlevlerin neredeyse her zaman IO veya RNG'yi değiştirmesi gerektiğinden, `!` ile biten işlevler, IO'yu değiştirmek veya RNG durumunu ilerletmek dışındaki bir değişimi belirtmek için kullanılır. Örneğin, `rand(x)` RNG'yi değiştirirken, `rand!(x)` hem RNG'yi hem de `x`'yi değiştirir; benzer şekilde, `read(io)` `io`'yu değiştirirken, `read!(io, x)` her iki argümanı da değiştirir.

## Avoid strange type `Union`s

`Union{Function,AbstractString}` gibi türler, genellikle bazı tasarımların daha temiz olabileceğinin bir işareti olarak kabul edilir.

## Avoid elaborate container types

Genellikle aşağıdaki gibi diziler oluşturmak pek faydalı değildir:

```julia
a = Vector{Union{Int,AbstractString,Tuple,Array}}(undef, n)
```

Bu durumda `Vector{Any}(undef, n)` daha iyidir. Ayrıca, belirli kullanımları (örneğin `a[i]::Int`) belirtmek, birçok alternatifi tek bir türde toplamaya çalışmaktan daha derleyiciye yardımcı olur.

## Prefer exported methods over direct field access

İdiomatik Julia kodu, genellikle bir modülün dışa aktarılan yöntemlerini türlerinin arayüzü olarak ele almalıdır. Bir nesnenin alanları genellikle uygulama detayları olarak kabul edilir ve kullanıcı kodu bunlara yalnızca API olarak belirtilmişse doğrudan erişmelidir. Bunun birkaç avantajı vardır:

  * Paket geliştiricileri, kullanıcı kodunu bozmadıkları sürece uygulamayı değiştirme konusunda daha özgürdür.
  * Yöntemler, [`map`](@ref) gibi yüksek düzeyli yapılarla (örneğin `map(imag, zs)`) geçilebilir, bunun yerine `[z.im for z in zs]` kullanılabilir.
  * Soyut türler üzerinde yöntemler tanımlanabilir.
  * Yöntemler, farklı türler arasında paylaşılabilen kavramsal bir işlemi tanımlayabilir (örneğin, `real(z)` Karmaşık sayılar veya Quaternionlar üzerinde çalışır).

Julia'nın dispatch sistemi bu tarzı teşvik eder çünkü `play(x::MyType)` yalnızca o belirli tür için `play` yöntemini tanımlar, diğer türlerin kendi uygulamalarına sahip olmasına izin verir.

Benzer şekilde, dışa aktarılmamış fonksiyonlar genellikle dahili olup değişime tabidir, aksi belirtilmedikçe. İsimlere bazen bir `_` ön eki (veya son eki) verilerek bir şeyin "dahili" veya bir uygulama detayı olduğu daha fazla vurgulanır, ancak bu bir kural değildir.

Karşı örnekler bu kuralı içerir [`NamedTuple`](@ref), [`RegexMatch`](@ref match), [`StatStruct`](@ref stat).

## Use naming conventions consistent with Julia `base/`

  * modüller ve tür adları büyük harf ve camel case kullanır: `module SparseArrays`, `struct UnitRange`.
  * functions are lowercase ([`maximum`](@ref), [`convert`](@ref)) and, when readable, with multiple words squashed together ([`isequal`](@ref), [`haskey`](@ref)). When necessary, use underscores as word separators. Underscores are also used to indicate a combination of concepts ([`remotecall_fetch`](@ref) as a more efficient implementation of `fetch(remotecall(...))`) or as modifiers.
  * fonksiyonlar, en az bir argümanını değiştirenler `!` ile biter.
  * kısalık değerlidir, ancak kısaltmalardan kaçının ([`indexin`](@ref) yerine `indxin` gibi) çünkü belirli kelimlerin kısaltılıp kısaltılmadığını hatırlamak zorlaşır.

Eğer bir fonksiyon adı birden fazla kelime gerektiriyorsa, bunun birden fazla kavramı temsil edip etmediğini düşünün ve parçalar halinde daha iyi bölünüp bölünemeyeceğini değerlendirin.

## Write functions with argument ordering similar to Julia Base

Genel bir kural olarak, Base kütüphanesi işlevlere geçilen argümanların aşağıdaki sırasını kullanır, uygulanabilir olduğunda:

1. **Fonksiyon argümanı**. Bir fonksiyon argümanını ilk sıraya koymak, çok satırlı anonim fonksiyonları geçmek için [`do`](@ref) bloklarının kullanılmasına izin verir.
2. **G/Ç akışı**. `IO` nesnesini ilk olarak belirtmek, [`sprint`](@ref) gibi fonksiyonlara fonksiyon geçirmeye izin verir, örneğin `sprint(show, x)`.
3. **Girdi değiştiriliyor**. Örneğin, [`fill!(x, v)`](@ref fill!) içinde, `x` değiştirilen nesnedir ve `x`'e eklenmesi gereken değerden önce görünür.
4. **Tür**. Bir tür geçmek genellikle çıktının verilen türde olacağı anlamına gelir. [`parse(Int, "1")`](@ref parse) içinde, tür ayrıştırılacak dizenin önündedir. Türün ilk geldiği birçok örnek vardır, ancak [`read(io, String)`](@ref read) içinde `IO` argümanının türden önce geldiğini not etmek faydalıdır; bu, burada belirtilen sıraya uygundur.
5. **Girdi değiştirilmedi**. `fill!(x, v)` içinde, `v` *değiştirilmiyor* ve `x`'ten sonra geliyor.
6. **Anahtar**. Birleştirici koleksiyonlar için, bu anahtar-değer çiftinin anahtarıdır. Diğer dizinlenmiş koleksiyonlar için, bu dizindir.
7. **Değer**. İlişkisel koleksiyonlar için, bu anahtar-değer çiftinin değeridir. [`fill!(x, v)`](@ref fill!) gibi durumlarda, bu `v`dir.
8. **Her şey**. Diğer tüm argümanlar.
9. **Varargs**. Bu, bir işlev çağrısının sonunda sonsuz sayıda argümanın listelenebileceğini ifade eder. Örneğin, `Matrix{T}(undef, dims)` ifadesinde, boyutlar [`Tuple`](@ref) olarak verilebilir, örneğin `Matrix{T}(undef, (1,2))` veya [`Vararg`](@ref) olarak verilebilir, örneğin `Matrix{T}(undef, 1, 2)`.
10. **Anahtar argümanlar**. Julia'da anahtar argümanlar, fonksiyon tanımlarında her durumda en sona gelmelidir; burada tamamlayıcılık açısından listelenmiştir.

Çoğu fonksiyon yukarıda listelenen her tür argümanı almaz; sayılar yalnızca bir fonksiyona uygulanabilir argümanlar için kullanılacak önceliği belirtir.

Elbette birkaç istisna vardır. Örneğin, [`convert`](@ref) içinde, tür her zaman önce gelmelidir. [`setindex!`](@ref) içinde ise, değer indekslerden önce gelir, böylece indeksler varargs olarak sağlanabilir.

API'leri tasarlarken, bu genel sıraya mümkün olduğunca uymak, fonksiyonlarınızın kullanıcılarına daha tutarlı bir deneyim sunma olasılığını artırır.

## Don't overuse try-catch

Hataları yakalamaya güvenmektense, onlardan kaçınmak daha iyidir.

## Don't parenthesize conditions

Julia koşullar etrafında parantez gerektirmez `if` ve `while`. Yaz:

```julia
if a == b
```

bunun yerine:

```julia
if (a == b)
```

## Don't overuse `...`

Fonksiyon argümanlarını birleştirmek bağımlılık yapabilir. `[a..., b...]` yerine, zaten dizileri birleştiren `[a; b]` kullanın. [`collect(a)`](@ref) `[a...]`'den daha iyidir, ancak `a` zaten yineleyici olduğundan, genellikle onu olduğu gibi bırakmak ve bir diziye dönüştürmemek daha iyidir.

## Ensure constructors return an instance of their own type

When a method `T(x)` is called on a type `T`, it is generally expected to return a value of type T. Defining a [constructor](@ref man-constructors) that returns an unexpected type can lead to confusing and unpredictable behavior:

```jldoctest
julia> struct Foo{T}
           x::T
       end

julia> Base.Float64(foo::Foo) = Foo(Float64(foo.x))  # Do not define methods like this

julia> Float64(Foo(3))  # Should return `Float64`
Foo{Float64}(3.0)

julia> Foo{Int}(x) = Foo{Float64}(x)  # Do not define methods like this

julia> Foo{Int}(3)  # Should return `Foo{Int}`
Foo{Float64}(3.0)
```

Kodun netliğini korumak ve tür tutarlılığını sağlamak için, her zaman oluşturulması gereken türün bir örneğini döndüren yapıcılar tasarlayın.

## Don't use unnecessary static parameters

Bir fonksiyon imzası:

```julia
foo(x::T) where {T<:Real} = ...
```

lütfen yazılmalıdır:

```julia
foo(x::Real) = ...
```

bunun yerine, özellikle `T` fonksiyon gövdesinde kullanılmıyorsa. `T` kullanılsa bile, uygun olduğunda [`typeof(x)`](@ref) ile değiştirilebilir. Performans farkı yoktur. Bunun genel bir statik parametre uyarısı olmadığını, sadece ihtiyaç duyulmadığı durumlarda kullanımlara karşı bir uyarı olduğunu unutmayın.

Not edin ki, konteyner türleri, özellikle işlev çağrılarında tür parametrelerine ihtiyaç duyabilir. Daha fazla bilgi için SSS [Avoid fields with abstract containers](@ref)'ya bakın.

## Avoid confusion about whether something is an instance or a type

Aşağıdaki gibi tanım setleri kafa karıştırıcıdır:

```julia
foo(::Type{MyType}) = ...
foo(::MyType) = foo(MyType)
```

Karar verin, sorulan kavram `MyType` mi yoksa `MyType()` mu olarak yazılacak ve buna sadık kalın.

Tercih edilen stil, varsayılan olarak örnekler kullanmaktır ve yalnızca `Type{MyType}` ile ilgili yöntemler eklenmelidir, eğer bazı sorunları çözmek için gerekli hale gelirse.

Eğer bir tür etkili bir şekilde bir enumerasyon ise, bu tür tek bir (ideali olarak değişmez bir yapı veya ilkel) tür olarak tanımlanmalı ve enumerasyon değerleri bunun örnekleri olmalıdır. Yapıcılar ve dönüşümler, değerlerin geçerli olup olmadığını kontrol edebilir. Bu tasarım, enumerasyonu soyut bir tür yapmak ve "değerleri" alt türler olarak tanımlamak yerine tercih edilmektedir.

## Don't overuse macros

Bir makronun gerçekten bir fonksiyon olabileceği zamanların farkında olun.

[`eval`](@ref) makrosu içinde çağrıldığında özellikle tehlikeli bir uyarı işareti; bu, makronun yalnızca en üst düzeyde çağrıldığında çalışacağı anlamına gelir. Böyle bir makro bir işlev olarak yazılırsa, doğal olarak ihtiyaç duyduğu çalışma zamanı değerlerine erişimi olacaktır.

## Don't expose unsafe operations at the interface level

Eğer yerel bir işaretçi kullanan bir türünüz varsa:

```julia
mutable struct NativeType
    p::Ptr{UInt8}
    ...
end
```

anlamları aşağıdaki gibi yazmayın:

```julia
getindex(x::NativeType, i) = unsafe_load(x.p, i)
```

Sorun, bu tür kullanıcıların `x[i]` yazabilmesidir; bu, işlemin güvensiz olduğunu fark etmeden yapılır ve ardından bellek hatalarına maruz kalabilirler.

Böyle bir fonksiyon, işlemin güvenli olduğunu kontrol etmeli ya da çağıranları uyarmak için adında `unsafe` kelimesini içermelidir.

## Don't overload methods of base container types

Aşağıdaki gibi tanımlar yazmak mümkündür:

```julia
show(io::IO, v::Vector{MyType}) = ...
```

Bu, belirli bir yeni öğe türü ile vektörlerin özel gösterimini sağlayacaktır. Cazip olsa da, bu kaçınılmalıdır. Sorun, kullanıcıların `Vector()` gibi iyi bilinen bir türün belirli bir şekilde davranmasını beklemesidir ve davranışını aşırı özelleştirmek, onunla çalışmayı zorlaştırabilir.

## [Avoid type piracy](@id avoid-type-piracy)

"Tip hırsızlığı", tanımlamadığınız türler üzerinde Base veya diğer paketlerdeki yöntemleri genişletme veya yeniden tanımlama uygulamasını ifade eder. Aşırı durumlarda, Julia'yı çökertmek mümkündür (örneğin, yöntem genişletmeniz veya yeniden tanımlamanız geçersiz bir girdinin `ccall`'e iletilmesine neden olursa). Tip hırsızlığı, kod hakkında düşünmeyi karmaşık hale getirebilir ve tahmin edilmesi ve teşhis edilmesi zor uyumsuzluklar ortaya çıkarabilir.

Bir örnek olarak, bir modüldeki semboller üzerinde çarpma tanımlamak istediğinizi varsayalım:

```julia
module A
import Base.*
*(x::Symbol, y::Symbol) = Symbol(x,y)
end
```

Sorun şu ki, artık `Base.*` kullanan diğer herhangi bir modül de bu tanımı görecek. `Symbol` Base'de tanımlandığı ve diğer modüller tarafından kullanıldığı için, bu, ilgisiz kodun davranışını beklenmedik bir şekilde değiştirebilir. Burada, farklı bir işlev adı kullanmak veya `Symbol`'ları tanımladığınız başka bir tür içinde sarmalamak gibi birkaç alternatif vardır.

Bazen, çift paketler, tanımları özelliklerden ayırmak için tür korsanlığına girebilir, özellikle de paketler işbirliği yapan yazarlar tarafından tasarlandığında ve tanımlar yeniden kullanılabilir olduğunda. Örneğin, bir paket renklerle çalışmak için yararlı bazı türler sağlayabilir; başka bir paket bu türler için renk alanları arasında dönüşümleri sağlayan yöntemler tanımlayabilir. Bir başka örnek, bazı C kodları için ince bir sarıcı işlevi gören bir paket olabilir; başka bir paket bu sarıcıyı, daha yüksek seviyeli, Julia dostu bir API uygulamak için korsanlayabilir.

## Be careful with type equality

Genellikle [`isa`](@ref) ve [`<:`](@ref) kullanmak istersiniz, `==` değil. Türleri tam eşitlik için kontrol etmek genellikle yalnızca bilinen bir somut türle karşılaştırırken (örneğin, `T == Float64`) veya *gerçekten, gerçekten* ne yaptığınızı biliyorsanız anlamlıdır.

## Don't write a trivial anonymous function `x->f(x)` for a named function `f`

Yüksek dereceli fonksiyonlar genellikle anonim fonksiyonlarla çağrıldığından, bunun arzu edilir veya hatta gerekli olduğu sonucuna varmak kolaydır. Ancak herhangi bir fonksiyon doğrudan, anonim bir fonksiyona "sarılmadan" geçirilebilir. `map(x->f(x), a)` yazmak yerine [`map(f, a)`](@ref) yazın.

## Avoid using floats for numeric literals in generic code when possible

Eğer sayıları işleyen genel bir kod yazıyorsanız ve bu kodun birçok farklı sayısal tür argümanıyla çalışması bekleniyorsa, argümanları mümkün olduğunca az etkileyecek bir sayısal türün sabitlerini kullanmayı deneyin.

Örneğin,

```jldoctest
julia> f(x) = 2.0 * x
f (generic function with 1 method)

julia> f(1//2)
1.0

julia> f(1/2)
1.0

julia> f(1)
2.0
```

while

```jldoctest
julia> g(x) = 2 * x
g (generic function with 1 method)

julia> g(1//2)
1//1

julia> g(1/2)
1.0

julia> g(1)
2
```

Gördüğünüz gibi, `Int` literal kullandığımız ikinci versiyon, giriş argümanının türünü korudu, ilk versiyon ise korumadı. Bunun nedeni, örneğin `promote_type(Int, Float64) == Float64` olmasıdır ve terfi çarpma ile gerçekleşir. Benzer şekilde, [`Rational`](@ref) literal'ları [`Float64`](@ref) literal'larından daha az tür bozucu, ancak `Int`'lerden daha bozucudur:

```jldoctest
julia> h(x) = 2//1 * x
h (generic function with 1 method)

julia> h(1//2)
1//1

julia> h(1/2)
1.0

julia> h(1)
2//1
```

Bu nedenle, kodunuzu kullanmayı kolaylaştırmak için mümkün olduğunda `Int` literalleri kullanın, tam sayı olmayan sayılar için `Rational{Int}` kullanın.
