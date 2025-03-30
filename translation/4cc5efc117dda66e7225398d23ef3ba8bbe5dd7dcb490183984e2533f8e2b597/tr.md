# More about types

Eğer bir süre Julia kullandıysanız, türlerin oynadığı temel rolü anlarsınız. Burada, özellikle [Parametric Types](@ref) üzerine odaklanarak, derinlemesine incelemeye çalışıyoruz.

## Types and sets (and `Any` and `Union{}`/`Bottom`)

Julia'nın tür sistemini setler açısından düşünmek belki de en kolay yoldur. Programlar bireysel değerlerle işlem yaparken, bir tür bir değerler kümesine atıfta bulunur. Bu, bir koleksiyonla aynı şey değildir; örneğin, bir [`Set`](@ref) değerler kümesi kendisi tek bir `Set` değeridir. Daha ziyade, bir tür *mümkün* değerler kümesini tanımlar ve hangi değere sahip olduğumuz konusunda belirsizlik ifade eder.

Bir *somut* tür `T`, [`typeof`](@ref) fonksiyonu tarafından döndürülen doğrudan etiketinin `T` olduğu değerler kümesini tanımlar. Bir *soyut* tür, muhtemelen daha büyük bir değer kümesini tanımlar.

[`Any`](@ref) evrenin olası değerlerinin tamamını tanımlar. [`Integer`](@ref) `Any`'nin bir alt kümesidir ve `Int`, [`Int8`](@ref) ve diğer somut türleri içerir. İçsel olarak, Julia ayrıca `Bottom` olarak bilinen başka bir türü de yoğun bir şekilde kullanır; bu da `Union{}` olarak yazılabilir. Bu, boş küme ile ilişkilidir.

Julia'nın türleri, küme teorisinin standart işlemlerini destekler: `T1`'in `T2`'nin "alt kümesi" (alt türü) olup olmadığını `T1 <: T2` ile sorabilirsiniz. Benzer şekilde, iki türü [`typeintersect`](@ref) ile kesiştirebilir, bunların birleşimini [`Union`](@ref) ile alabilir ve birleşimlerini içeren bir türü [`typejoin`](@ref) ile hesaplayabilirsiniz:

```jldoctest
julia> typeintersect(Int, Float64)
Union{}

julia> Union{Int, Float64}
Union{Float64, Int64}

julia> typejoin(Int, Float64)
Real

julia> typeintersect(Signed, Union{UInt8, Int8})
Int8

julia> Union{Signed, Union{UInt8, Int8}}
Union{UInt8, Signed}

julia> typejoin(Signed, Union{UInt8, Int8})
Integer

julia> typeintersect(Tuple{Integer, Float64}, Tuple{Int, Real})
Tuple{Int64, Float64}

julia> Union{Tuple{Integer, Float64}, Tuple{Int, Real}}
Union{Tuple{Int64, Real}, Tuple{Integer, Float64}}

julia> typejoin(Tuple{Integer, Float64}, Tuple{Int, Real})
Tuple{Integer, Real}
```

Bu işlemler soyut görünebilirken, Julia'nın kalbinde yer alır. Örneğin, yöntem dağıtımı, bir yöntem listesindeki öğeleri adım adım geçerek, argüman demetinin türünün yöntem imzasının bir alt türü olduğu birine ulaşana kadar gerçekleştirilir. Bu algoritmanın çalışabilmesi için, yöntemlerin özgüllüklerine göre sıralanması ve aramanın en özgül yöntemlerle başlaması önemlidir. Sonuç olarak, Julia ayrıca türler üzerinde kısmi bir sıralama uygular; bu, `<:` ile benzer bir işlevsellik ile sağlanır, ancak aşağıda tartışılacak farklılıklarla birlikte.

## UnionAll types

Julia'nın tür sistemi ayrıca bir *tekrarlanan birleşim* türlerini ifade edebilir: bir değişkenin tüm değerleri üzerindeki türlerin birleşimi. Bu, bazı parametrelerin değerlerinin bilinmediği parametrik türleri tanımlamak için gereklidir.

Örneğin, [`Array`](@ref) iki parametreye sahiptir, `Array{Int,2}` şeklinde. Eleman tipini bilmiyorsak, `Array{T,2} where T` yazabiliriz; bu, `T` için tüm değerlerin `Array{T,2}` birleşimidir: `Union{Array{Int8,2}, Array{Int16,2}, ...}`.

Böyle bir tür, bir değişken (`T` bu örnekte, `TypeVar` türünde) ve bir sarılı tür (`Array{T,2}` bu örnekte) içeren bir `UnionAll` nesnesi ile temsil edilir.

Aşağıdaki yöntemleri dikkate alın:

```julia
f1(A::Array) = 1
f2(A::Array{Int}) = 2
f3(A::Array{T}) where {T<:Any} = 3
f4(A::Array{Any}) = 4
```

İmza - [Function calls](@ref Function-calls) olarak tanımlandığı gibi - `f3`'ün bir `UnionAll` türü olduğu ve bir demet türünü sarmaladığı: `Tuple{typeof(f3), Array{T}} where T`. `f4` hariç hepsi `a = [1,2]` ile çağrılabilir; `f2` hariç hepsi `b = Any[1,2]` ile çağrılabilir.

Bu türlere biraz daha yakından bakalım:

```jldoctest
julia> dump(Array)
UnionAll
  var: TypeVar
    name: Symbol T
    lb: Union{}
    ub: Any
  body: UnionAll
    var: TypeVar
      name: Symbol N
      lb: Union{}
      ub: Any
    body: Array{T, N} <: DenseArray{T, N}
      ref::MemoryRef{T}
      size::NTuple{N, Int64}
```

Bu, `Array`'ın aslında bir `UnionAll` türünü adlandırdığını gösterir. Her parametre için bir `UnionAll` türü vardır, iç içe geçmiş. `Array{Int,2}` sözdizimi, `Array{Int}{2}` ile eşdeğerdir; dahili olarak her `UnionAll`, belirli bir değişken değeri ile, bir seferde, en dıştaki ilk olarak örneklendirilir. Bu, sonlandırıcı tür parametrelerinin atlanmasına doğal bir anlam kazandırır; `Array{Int}`, `Array{Int,N} where N` ile eşdeğer bir tür verir.

Bir `TypeVar`, kendisi bir tür değildir, daha ziyade bir `UnionAll` türünün yapısının bir parçası olarak düşünülmelidir. Tür değişkenlerinin değerleri üzerinde alt ve üst sınırları vardır (sırasıyla `lb` ve `ub` alanlarında). `name` sembolü tamamen kozmetiktir. Dahili olarak, `TypeVar`lar adresle karşılaştırılır, bu nedenle "farklı" tür değişkenlerinin ayırt edilebilmesi için değiştirilebilir türler olarak tanımlanırlar. Ancak, geleneksel olarak değiştirilmemeleri gerekir.

Bir `TypeVar`'ı manuel olarak oluşturmak mümkündür:

```jldoctest
julia> TypeVar(:V, Signed, Real)
Signed<:V<:Real
```

Bu `name` sembolü hariç bu argümanlardan herhangi birini atlamanıza izin veren pratik versiyonlar vardır.

`Array{T} where T<:Integer` ifadesi aşağıdaki şekilde düşürülür:

```julia
let T = TypeVar(:T,Integer)
    UnionAll(T, Array{T})
end
```

bu nedenle bir `TypeVar`'ı manuel olarak oluşturmak nadiren gereklidir (aslında, bu kaçınılması gereken bir durumdur).

## Free variables

*Serbest* bir tür değişkeni kavramı, tür sisteminde son derece önemlidir. Bir değişkenin `V`, tür `T` içinde serbest olduğunu söyleriz eğer `T`, değişken `V`'yi tanıtan `UnionAll` içermez. Örneğin, `Array{Array{V} where V<:Integer}` türü serbest değişken içermez, ancak içindeki `Array{V}` kısmı bir serbest değişken, `V` içerir.

Serbest değişkenlere sahip bir tür, bir anlamda, gerçekten bir tür değildir. `Array{Array{T}} where T` türünü düşünün; bu, tüm homojen dizi dizilerine atıfta bulunur. İç tür `Array{T}`, kendi başına incelendiğinde, her türlü diziye atıfta bulunuyormuş gibi görünebilir. Ancak, dış dizinin her bir elemanı *aynı* dizi türüne sahip olmalıdır, bu nedenle `Array{T}` sadece herhangi bir eski diziye atıfta bulunamaz. `Array{T}`'nin etkili bir şekilde "birden fazla kez" "bulunduğu" söylenebilir ve `T` her "kez" aynı değere sahip olmalıdır.

Bu nedenle, C API'deki `jl_has_free_typevars` fonksiyonu çok önemlidir. Doğru döndüğü türler, alt türleme ve diğer tür fonksiyonlarında anlamlı yanıtlar vermez.

## TypeNames

Aşağıdaki iki [`Array`](@ref) türü işlevsel olarak eşdeğerdir, ancak farklı şekilde yazdırır:

```jldoctest
julia> TV, NV = TypeVar(:T), TypeVar(:N)
(T, N)

julia> Array
Array

julia> Array{TV, NV}
Array{T, N}
```

Bunlar, `TypeName` türünde bir nesne olan `name` alanını inceleyerek ayırt edilebilir:

```julia-repl
julia> dump(Array{Int,1}.name)
TypeName
  name: Symbol Array
  module: Module Core
  names: empty SimpleVector
  wrapper: UnionAll
    var: TypeVar
      name: Symbol T
      lb: Union{}
      ub: Any
    body: UnionAll
      var: TypeVar
        name: Symbol N
        lb: Union{}
        ub: Any
      body: Array{T, N} <: DenseArray{T, N}
  cache: SimpleVector
    ...

  linearcache: SimpleVector
    ...

  hash: Int64 -7900426068641098781
  mt: MethodTable
    name: Symbol Array
    defs: Nothing nothing
    cache: Nothing nothing
    max_args: Int64 0
    module: Module Core
    : Int64 0
    : Int64 0
```

Bu durumda, ilgili alan `wrapper`dır; bu, yeni `Array` türleri oluşturmak için kullanılan üst düzey türüne bir referans tutar.

```julia-repl
julia> pointer_from_objref(Array)
Ptr{Cvoid} @0x00007fcc7de64850

julia> pointer_from_objref(Array.body.body.name.wrapper)
Ptr{Cvoid} @0x00007fcc7de64850

julia> pointer_from_objref(Array{TV,NV})
Ptr{Cvoid} @0x00007fcc80c4d930

julia> pointer_from_objref(Array{TV,NV}.name.wrapper)
Ptr{Cvoid} @0x00007fcc7de64850
```

`wrapper` alanı [`Array`](@ref) kendisine işaret eder, ancak `Array{TV,NV}` için türün orijinal tanımına geri işaret eder.

Diğer alanlar hakkında ne dersiniz? `hash`, her tür için bir tamsayı atar. `cache` alanını incelemek için, Array'den daha az kullanılan bir tür seçmek faydalıdır. Öncelikle kendi türümüzü oluşturalım:

```jldoctest
julia> struct MyType{T,N} end

julia> MyType{Int,2}
MyType{Int64, 2}

julia> MyType{Float32, 5}
MyType{Float32, 5}
```

Parametrik bir türü örneklendirdiğinizde, her somut tür bir tür önbelleğine kaydedilir (`MyType.body.body.name.cache`). Ancak, serbest tür değişkenleri içeren örnekler önbelleğe alınmaz.

## Tuple types

Tuple türleri ilginç bir özel durumu oluşturur. `x::Tuple` gibi bildirimlerde dağıtımın çalışabilmesi için türün herhangi bir tuple'ı barındırabilmesi gerekir. Parametreleri kontrol edelim:

```jldoctest
julia> Tuple
Tuple

julia> Tuple.parameters
svec(Vararg{Any})
```

Diğer türlerden farklı olarak, demet türleri parametrelerinde kovaryandır, bu nedenle bu tanım `Tuple`'ın herhangi bir demet türüyle eşleşmesine izin verir:

```jldoctest
julia> typeintersect(Tuple, Tuple{Int,Float64})
Tuple{Int64, Float64}

julia> typeintersect(Tuple{Vararg{Any}}, Tuple{Int,Float64})
Tuple{Int64, Float64}
```

Ancak, eğer bir değişken sayıda (`Vararg`) demet türü serbest değişkenlere sahipse, farklı türde demetleri tanımlayabilir:

```jldoctest
julia> typeintersect(Tuple{Vararg{T} where T}, Tuple{Int,Float64})
Tuple{Int64, Float64}

julia> typeintersect(Tuple{Vararg{T}} where T, Tuple{Int,Float64})
Union{}
```

`T`'nin `Tuple` türü ile ilgili olarak serbest olduğunu (yani bağlama `UnionAll` türünün `Tuple` türünün dışında olduğunu) fark edin, yalnızca bir `T` değeri tüm tür üzerinde çalışmalıdır. Bu nedenle, heterojen bir demet eşleşmez.

Son olarak, `Tuple{}`'ın farklı olduğunu belirtmek gerekir:

```jldoctest
julia> Tuple{}
Tuple{}

julia> Tuple{}.parameters
svec()

julia> typeintersect(Tuple{}, Tuple{Int})
Union{}
```

"Birincil" tuple türü nedir?

```julia-repl
julia> pointer_from_objref(Tuple)
Ptr{Cvoid} @0x00007f5998a04370

julia> pointer_from_objref(Tuple{})
Ptr{Cvoid} @0x00007f5998a570d0

julia> pointer_from_objref(Tuple.name.wrapper)
Ptr{Cvoid} @0x00007f5998a04370

julia> pointer_from_objref(Tuple{}.name.wrapper)
Ptr{Cvoid} @0x00007f5998a04370
```

yani `Tuple == Tuple{Vararg{Any}}` gerçekten de birincil türdür.

## Diagonal types

`Tuple{T,T} where T` türünü düşünün. Bu imzaya sahip bir yöntem şöyle görünecektir:

```julia
f(x::T, y::T) where {T} = ...
```

`UnionAll` türünün yaygın yorumuna göre, bu `T` tüm türler üzerinde, `Any` dahil, değişir, bu nedenle bu tür `Tuple{Any,Any}` ile eşdeğer olmalıdır. Ancak, bu yorum bazı pratik sorunlara yol açmaktadır.

Öncelikle, `T` değerinin yöntem tanımı içinde mevcut olması gerekir. `f(1, 1.0)` gibi bir çağrı için, `T`'nin ne olması gerektiği net değildir. `Union{Int,Float64}` olabilir veya belki de [`Real`](@ref) olabilir. İçgüdüsel olarak, `x::T` ifadesinin `T === typeof(x)` anlamına geldiğini bekleriz. Bu invarianın sağlandığından emin olmak için, bu yöntemde `typeof(x) === typeof(y) === T` olmalıdır. Bu, yöntemin yalnızca tam olarak aynı türdeki argümanlar için çağrılması gerektiği anlamına gelir.

İki değerin aynı tipe sahip olup olmadığını belirlemenin çok faydalı olduğu ortaya çıkıyor (bu, örneğin, terfi sistemi tarafından kullanılıyor), bu yüzden `Tuple{T,T} where T` ifadesinin farklı bir yorumuna ihtiyaç duymamız için birden fazla nedenimiz var. Bunu çalıştırmak için, alt türlendirmeye aşağıdaki kuralı ekliyoruz: Eğer bir değişken, kovaryant pozisyonda birden fazla kez geçiyorsa, yalnızca somut türler üzerinde değişiklik yapmasıyla sınırlıdır. ("Kovaryant pozisyon", bir değişkenin bir örneği ile onu tanıtan `UnionAll` türü arasında yalnızca `Tuple` ve `Union` türlerinin bulunduğu anlamına gelir.) Bu tür değişkenlere "diyagonal değişkenler" veya "somut değişkenler" denir.

Örneğin, `Tuple{T,T} where T` ifadesi `Union{Tuple{Int8,Int8}, Tuple{Int16,Int16}, ...}` olarak görülebilir; burada `T` tüm somut türler üzerinde değişir. Bu, bazı ilginç alt türleme sonuçlarına yol açar. Örneğin, `Tuple{Real,Real}` ifadesi `Tuple{T,T} where T`'nin bir alt türü değildir, çünkü iki elemanın farklı türlere sahip olduğu `Tuple{Int8,Int16}` gibi bazı türleri içerir. `Tuple{Real,Real}` ve `Tuple{T,T} where T`'nin `Tuple{T,T} where T<:Real` olan önemsiz kesişimi vardır. Ancak, `Tuple{Real}` *bir* alt türdür `Tuple{T} where T` ifadesinin, çünkü bu durumda `T` yalnızca bir kez geçer ve bu nedenle çapraz değildir.

Sonra aşağıdaki gibi bir imzayı düşünün:

```julia
f(a::Array{T}, x::T, y::T) where {T} = ...
```

Bu durumda, `T` `Array{T}` içinde değişmez bir konumda yer alır. Bu, hangi tür dizinin geçildiğinin `T` değerini belirsiz bir şekilde belirlediği anlamına gelir - `T` üzerinde bir *eşitlik kısıtlaması* olduğunu söyleriz. Bu nedenle, bu durumda diyagonal kural gerçekten gerekli değildir, çünkü dizi `T`'yi belirler ve ardından `x` ve `y`'nin `T`'nin herhangi bir alt türü olmasına izin verebiliriz. Bu nedenle, değişmez konumda yer alan değişkenler asla diyagonal olarak kabul edilmez. Bu davranış seçimi biraz tartışmalıdır - bazıları bu tanımın şöyle yazılması gerektiğini düşünüyor:

```julia
f(a::Array{T}, x::S, y::S) where {T, S<:T} = ...
```

`x` ve `y`'nin aynı türde olup olmadığını netleştirmek için. Bu imza versiyonunda öyle olacak, ya da `x` ve `y` farklı türlerde olabiliyorsa `y`'nin türü için üçüncü bir değişken tanıtabiliriz.

Bir sonraki komplikasyon, sendikaların ve çapraz değişkenlerin etkileşimidir, örneğin

```julia
f(x::Union{Nothing,T}, y::T) where {T} = ...
```

Bu beyanın ne anlama geldiğini düşünün. `y` tipi `T`'dir. `x` o zaman ya aynı tip `T`'ye sahip olabilir ya da [`Nothing`](@ref) tipinde olabilir. Bu nedenle, aşağıdaki tüm çağrılar eşleşmelidir:

```julia
f(1, 1)
f("", "")
f(2.0, 2.0)
f(nothing, 1)
f(nothing, "")
f(nothing, 2.0)
```

Bu örnekler bize bir şey söylüyor: `x` `nothing::Nothing` olduğunda, `y` üzerinde ekstra kısıtlamalar yoktur. Sanki yöntem imzasında `y::Any` varmış gibi. Gerçekten de, aşağıdaki tür eşitliğine sahibiz:

```julia
(Tuple{Union{Nothing,T},T} where T) == Union{Tuple{Nothing,Any}, Tuple{T,T} where T}
```

Genel kural şudur: bir somut değişken, kovaryant pozisyonda yalnızca bir kez kullanılıyorsa, somut değilmiş gibi davranır. `x`'in tipi `Nothing` olduğunda, `Union{Nothing,T}`'de `T`'yi kullanmamıza gerek yoktur; yalnızca ikinci slotta kullanırız. Bu, `Tuple{T} where T`'de `T`'yi somut türlerle kısıtlamanın hiçbir fark yaratmadığı gözlemiyle doğal olarak ortaya çıkar; tür, her iki durumda da `Tuple{Any}` ile eşittir.

Ancak, *değişmez* konumda görünmek, bir değişkenin somut olmasını engeller; bu değişkenin kullanılıp kullanılmadığına bakılmaksızın. Aksi takdirde, türler karşılaştırıldıkları diğer türlere bağlı olarak farklı davranabilir, bu da alt türlemenin geçişli olmamasına neden olur. Örneğin, düşünün

```julia
Tuple{Int,Int8,Vector{Integer}} <: Tuple{T,T,Vector{Union{Integer,T}}} where T
```

Eğer `Union` içindeki `T` göz ardı edilirse, o zaman `T` somut hale gelir ve cevap "yanlış" olur çünkü ilk iki tür aynı değildir. Ama bunun yerine düşünün

```julia
Tuple{Int,Int8,Vector{Any}} <: Tuple{T,T,Vector{Union{Integer,T}}} where T
```

Artık `Union` içindeki `T`'yi göz ardı edemeyiz (bizim `T == Any` olması gerekir), bu nedenle `T` somut değildir ve cevap "doğru"dur. Bu, `T`'nin somutluğunun diğer tipe bağlı olmasını gerektirir ki bu kabul edilemez çünkü bir tipin kendi başına net bir anlamı olmalıdır. Bu nedenle, `T`'nin `Vector` içinde görünümü her iki durumda da dikkate alınır.

## Subtyping diagonal variables

Diyagonal değişkenler için alt türleme algoritmasının iki bileşeni vardır: (1) değişken oluşumlarını tanımlamak ve (2) diyagonal değişkenlerin yalnızca somut türler üzerinde değişim göstermesini sağlamaktır.

İlk görev, ortamda her değişken için `occurs_inv` ve `occurs_cov` sayaçlarını ( `src/subtype.c` içinde) tutarak, sırasıyla invariant ve kovaryant oluşumların sayısını takip etmektir. Bir değişken, `occurs_inv == 0 && occurs_cov > 1` olduğunda diyagonal olarak kabul edilir.

İkinci görev, bir değişkenin alt sınırı üzerinde bir koşul koyarak gerçekleştirilir. Alt türleme algoritması çalışırken, her değişkenin sınırlarını daraltır (alt sınırları yükseltir ve üst sınırları düşürür) ve alt tür ilişkisini koruyacak değişken değerleri aralığını takip eder. `UnionAll` türünün, değişkenin diyagonal olduğu gövdesini değerlendirmeyi tamamladığımızda, sınırların son değerlerine bakarız. Değişken somut olmalı olduğundan, alt sınırı somut bir türün alt türü olamazsa bir çelişki meydana gelir. Örneğin, [`AbstractArray`](@ref) gibi soyut bir tür, somut bir türün alt türü olamaz, ancak `Int` gibi somut bir tür olabilir ve boş tür `Bottom` da olabilir. Eğer bir alt sınır bu testi geçemezse, algoritma `false` yanıtıyla durur.

Örneğin, `Tuple{Int,String} <: Tuple{T,T} where T` probleminde, bunun doğru olacağını, `T`'nin `Union{Int,String}`'in bir üst türü olması durumunda çıkarıyoruz. Ancak, `Union{Int,String}` soyut bir türdür, bu nedenle ilişki geçerli değildir.

Bu somutluk testi `is_leaf_bound` fonksiyonu ile yapılır. Bu testin `jl_is_leaf_type`'dan biraz farklı olduğunu unutmayın, çünkü `Bottom` için de `true` döndürür. Şu anda bu fonksiyon sezgisel bir yöntemdir ve tüm olası somut türleri yakalamaz. Zorluk, bir alt sınırın somut olup olmadığının diğer tür değişken sınırlarının değerlerine bağlı olabilmesidir. Örneğin, `Vector{T}` yalnızca `T`'nin hem üst hem de alt sınırları `Int` eşit olduğunda somut tür `Vector{Int}` ile eşdeğerdir. Bunun için henüz tam bir algoritma geliştirmedik.

## Introduction to the internal machinery

Çeşitlerle ilgili işlemlerin çoğu `jltypes.c` ve `subtype.c` dosyalarında bulunur. Başlamak için iyi bir yol, alt türlerin nasıl çalıştığını izlemektir. Julia'yı `make debug` ile derleyin ve bir hata ayıklayıcı içinde Julia'yı başlatın. [gdb debugging tips](@ref gdb-debugging-tips) bazı yararlı ipuçları içermektedir.

Çünkü alt tür kodu REPL'de yoğun bir şekilde kullanılıyor - bu nedenle bu koddaki kesme noktaları sık sık tetikleniyor - aşağıdaki tanımı yapmanız en kolay olacaktır:

```julia-repl
julia> function mysubtype(a,b)
           ccall(:jl_breakpoint, Cvoid, (Any,), nothing)
           a <: b
       end
```

ve sonra `jl_breakpoint` içinde bir kesme noktası ayarlayın. Bu kesme noktası tetiklendiğinde, diğer fonksiyonlarda kesme noktaları ayarlayabilirsiniz.

Bir ısınma olarak, aşağıdakileri deneyin:

```julia
mysubtype(Tuple{Int, Float64}, Tuple{Integer, Real})
```

Daha karmaşık bir durum deneyerek daha ilginç hale getirebiliriz:

```julia
mysubtype(Tuple{Array{Int,2}, Int8}, Tuple{Array{T}, T} where T)
```

## Subtyping and method sorting

`type_morespecific` fonksiyonları, yöntem tablolarındaki fonksiyonlar üzerinde kısmi bir sıralama uygulamak için kullanılır (en özelden en az özel olana). Özelik katıdır; eğer `a`, `b`'den daha özel ise, o zaman `a`, `b`'ye eşit değildir ve `b`, `a`'dan daha özel değildir.

Eğer `a`, `b`'nin katı bir alt türü ise, otomatik olarak daha spesifik olarak kabul edilir. Buradan, `type_morespecific` bazı daha az resmi kuralları kullanır. Örneğin, `subtype` argüman sayısına duyarlıdır, ancak `type_morespecific` olmayabilir. Özellikle, `Tuple{Int,AbstractFloat}`, `Tuple{Integer}`'dan daha spesifiktir, hatta bir alt tür değildir. (`Tuple{Int,AbstractFloat}` ve `Tuple{Integer,Float64}`'den hiçbiri diğerinden daha spesifik değildir.) Benzer şekilde, `Tuple{Int,Vararg{Int}}`, `Tuple{Integer}`'nın bir alt türü değildir, ancak daha spesifik olarak kabul edilir. Ancak, `morespecific` uzunluk için bir bonus alır: özellikle, `Tuple{Int,Int}`, `Tuple{Int,Vararg{Int}}`'den daha spesifiktir.

Eğer yöntemlerin nasıl sıralandığını hata ayıklıyorsanız, fonksiyonu tanımlamak faydalı olabilir:

```julia
type_morespecific(a, b) = ccall(:jl_type_morespecific, Cint, (Any,Any), a, b)
```

hangi, `a` tuple türünün `b` tuple türünden daha özel olup olmadığını test etmenizi sağlar.
