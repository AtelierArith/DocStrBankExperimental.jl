```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/stdlib/Random/docs/src/index.md"
```

# Random Numbers

```@meta
DocTestSetup = :(using Random)
```

Julia'da rastgele sayı üretimi varsayılan olarak [Xoshiro256++](https://prng.di.unimi.it/) algoritmasını kullanır ve her `Task` için bir durum içerir. Diğer RNG türleri, `AbstractRNG` türünden miras alarak entegre edilebilir; bu türler daha sonra birden fazla rastgele sayı akışı elde etmek için kullanılabilir.

`Random` paketinden dışa aktarılan PRNG'ler (sahte rastgele sayı üreteçleri) şunlardır:

  * `TaskLocalRNG`: şu anda aktif olan Görev-eşel (Task-local) akışının kullanımını temsil eden bir token, ana görevden belirleyici bir şekilde tohumlanmış veya program başlangıcında `RandomDevice` (sistem rastgeleliği ile) tarafından tohumlanmıştır.
  * `Xoshiro`: Xoshiro256++ algoritmasını kullanarak küçük bir durum vektörü ile yüksek performanslı ve yüksek kaliteli rastgele sayı akışları üretir.
  * `RandomDevice`: OS tarafından sağlanan entropi için. Bu, kriptografik olarak güvenli rastgele sayılar (CS(P)RNG) için kullanılabilir.
  * `MersenneTwister`: eski Julia sürümlerinde varsayılan olan, alternatif bir yüksek kaliteli PRNG'dir ve oldukça hızlıdır, ancak durum vektörünü depolamak ve rastgele bir dizi oluşturmak için çok daha fazla alan gerektirir.

Çoğu rastgele üretimle ilgili fonksiyon, ilk argüman olarak isteğe bağlı bir `AbstractRNG` nesnesi alır. Bazıları ayrıca rastgele değerler dizileri oluşturmak için boyut spesifikasyonları `dims...` (bir demet olarak da verilebilir) alır. Çok iş parçacıklı bir programda, genellikle iş parçacıkları veya görevler için farklı RNG nesneleri kullanmalısınız, böylece iş parçacığı güvenliğini sağlarsınız. Ancak, varsayılan RNG, Julia 1.3 itibarıyla iş parçacığı güvenlidir (1.6 sürümüne kadar iş parçacığı başına RNG kullanarak ve sonrasında görev başına RNG kullanarak).

Verilen RNG'ler aşağıdaki türlerde uniform rastgele sayılar üretebilir: [`Float16`](@ref), [`Float32`](@ref), [`Float64`](@ref), [`BigFloat`](@ref), [`Bool`](@ref), [`Int8`](@ref), [`UInt8`](@ref), [`Int16`](@ref), [`UInt16`](@ref), [`Int32`](@ref), [`UInt32`](@ref), [`Int64`](@ref), [`UInt64`](@ref), [`Int128`](@ref), [`UInt128`](@ref), [`BigInt`](@ref) (veya bu türlerin karmaşık sayıları). Rastgele kayan nokta sayıları $[0, 1)$ aralığında uniform olarak üretilir. `BigInt` sınırsız tam sayıları temsil ettiğinden, aralığın belirtilmesi gerekir (örneğin `rand(big.(1:6))`).

Ayrıca, bazı `AbstractFloat` ve `Complex` türleri için normal ve üstel dağılımlar uygulanmıştır, ayrıntılar için [`randn`](@ref) ve [`randexp`](@ref)'ya bakın.

Rastgele sayılar üretmek için diğer dağılımlardan, [Distributions.jl](https://juliastats.org/Distributions.jl/stable/) paketine bakın.

!!! warning
    Rastgele sayıların üretilme şekli bir uygulama detayı olarak kabul edildiğinden, hata düzeltmeleri ve hız iyileştirmeleri, bir sürüm değişikliğinden sonra üretilen sayı akışını değiştirebilir. Birim testleri sırasında belirli bir tohum veya üretilen sayı akışına güvenmek bu nedenle önerilmez - bunun yerine söz konusu yöntemlerin özelliklerini test etmeyi düşünün.


## Random numbers module

```@docs
Random.Random
```

## Random generation functions

```@docs
Random.rand
Random.rand!
Random.bitrand
Random.randn
Random.randn!
Random.randexp
Random.randexp!
Random.randstring
```

## Subsequences, permutations and shuffling

```@docs
Random.randsubseq
Random.randsubseq!
Random.randperm
Random.randperm!
Random.randcycle
Random.randcycle!
Random.shuffle
Random.shuffle!
```

## Generators (creation and seeding)

```@docs
Random.default_rng
Random.seed!
Random.AbstractRNG
Random.TaskLocalRNG
Random.Xoshiro
Random.MersenneTwister
Random.RandomDevice
```

## [Hooking into the `Random` API](@id rand-api-hook)

`Random` işlevselliğini genişletmenin iki çoğunlukla ortogonal yolu vardır:

1. özel türlerin rastgele değerlerini oluşturma
2. yeni jeneratörler oluşturma

The API for 1) is quite functional, but is relatively recent so it may still have to evolve in subsequent releases of the `Random` module. For example, it's typically sufficient to implement one `rand` method in order to have all other usual methods work automatically.

The API for 2) is still rudimentary, and may require more work than strictly necessary from the implementor, in order to support usual types of generated values.

### Generating random values of custom types

Rastgele değerler üretmek bazı dağılımlar için çeşitli ticaret dengeleri içerebilir. *Önceden hesaplanmış* değerler, örneğin, ayrık dağılımlar için bir [alias table](https://en.wikipedia.org/wiki/Alias_method) veya tek değişkenli dağılımlar için [“squeezing” functions](https://en.wikipedia.org/wiki/Rejection_sampling) gibi değerler, örnekleme hızını önemli ölçüde artırabilir. Önceden ne kadar bilginin hesaplanması gerektiği, bir dağılımdan çekmeyi planladığımız değerlerin sayısına bağlı olabilir. Ayrıca, bazı rastgele sayı üreteçleri, çeşitli algoritmaların faydalanmak isteyebileceği belirli özelliklere sahip olabilir.

`Random` modülü, bu sorunları ele alabilecek rastgele değerler elde etmek için özelleştirilebilir bir çerçeve tanımlar. `rand`'in her çağrısı, yukarıdaki ticaret dengeleri göz önünde bulundurularak özelleştirilebilen bir *örnekleyici* oluşturur; bu, `Sampler`'a yöntemler ekleyerek yapılır ve bu yöntemler, rastgele sayı üreteci, dağılımı tanımlayan nesne ve tekrar sayısı için bir öneri üzerinde dağıtım yapabilir. Şu anda, sonuncusu için `Val{1}` (tek bir örnek için) ve `Val{Inf}` (keyfi bir sayı için) kullanılmakta olup, `Random.Repetition` her ikisi için de bir takma addır.

`Sampler` tarafından döndürülen nesne, rastgele değerleri üretmek için kullanılır. Örnekleme yapılabilen bir değer `X` için rastgele üretim arayüzünü uygularken, uygulayıcı aşağıdaki yöntemi tanımlamalıdır.

```julia
rand(rng, sampler)
```

`Sampler(rng, X, repetition)` tarafından döndürülen belirli `sampler` için.

Samplerlere `rand(rng, sampler)` uygulayan rastgele değerler olarak tanımlanabilir, ancak çoğu uygulama için aşağıdaki önceden tanımlanmış samplerlere yeterli olabilir:

1. `SamplerType{T}()` türünden `T`'den örnekler çizen örnekleyiciler uygulamak için kullanılabilir (örneğin, `rand(Int)`). Bu, *türler* için `Sampler` tarafından döndürülen varsayılan değerdir.
2. `SamplerTrivial(self)` basit bir sarmalayıcıdır ve `[]` ile erişilebilir. Önceden hesaplanmış bilgiye ihtiyaç duyulmadığında (örneğin, `rand(1:3)`) önerilen örnekleyicidir ve *değerler* için `Sampler` tarafından döndürülen varsayılandır.
3. `SamplerSimple(self, data)` ayrıca, `Sampler`'ın *özel bir yönteminde* hesaplanması gereken rastgele önceden hesaplanmış değerleri depolamak için kullanılabilecek ek `data` alanını içerir.

Herhangi birinin örneklerini sağlıyoruz. Burada algoritma seçimimizin RNG'den bağımsız olduğunu varsayıyoruz, bu nedenle imzalarımızda `AbstractRNG` kullanıyoruz.

```@docs
Random.Sampler
Random.SamplerType
Random.SamplerTrivial
Random.SamplerSimple
```

Önceden hesaplamayı değerleri gerçekten üretmekten ayırmak, API'nin bir parçasıdır ve kullanıcıya da açıktır. Örneğin, `rand(rng, 1:20)`'nin bir döngüde tekrar tekrar çağrılması gerektiğini varsayalım: bu ayrımın avantajlarından yararlanmanın yolu aşağıdaki gibidir:

```julia
rng = Xoshiro()
sp = Random.Sampler(rng, 1:20) # or Random.Sampler(Xoshiro, 1:20)
for x in X
    n = rand(rng, sp) # similar to n = rand(rng, 1:20)
    # use n
end
```

Bu, standart kütüphanede de kullanılan mekanizmadır; örneğin, rastgele dizi oluşturmanın varsayılan uygulaması (örneğin `rand(1:20, 10)` gibi).

#### Generating values from a type

Verilen bir `T` türü için, `rand(T)` tanımlıysa, `T` türünde bir nesne üretileceği varsayılmaktadır. `SamplerType`, türler için *varsayılan örnekleyicidir*. `T` türündeki değerlerin rastgele üretilmesini tanımlamak için, `rand(rng::AbstractRNG, ::Random.SamplerType{T})` yöntemi tanımlanmalı ve `rand(rng, T)`'nin beklediği değerleri döndürmelidir.

Aşağıdaki örneği ele alalım: `1` ile `n` arasında numaralandırılmış, `n` sayıda kenarı olan bir `Die` türü uyguluyoruz. `rand(Die)`'nin en az 4 ve en fazla 20 kenara sahip rastgele bir `Die` üretmesini istiyoruz.

```jldoctest Die
struct Die
    nsides::Int # number of sides
end

Random.rand(rng::AbstractRNG, ::Random.SamplerType{Die}) = Die(rand(rng, 4:20))

# output

```

`Die` için skalar ve dizi yöntemleri artık beklenildiği gibi çalışıyor:

```jldoctest Die; setup = :(Random.seed!(1))
julia> rand(Die)
Die(5)

julia> rand(Xoshiro(0), Die)
Die(10)

julia> rand(Die, 3)
3-element Vector{Die}:
 Die(9)
 Die(15)
 Die(14)

julia> a = Vector{Die}(undef, 3); rand!(a)
3-element Vector{Die}:
 Die(19)
 Die(7)
 Die(17)
```

#### A simple sampler without pre-computed data

Burada bir koleksiyon için bir örnekleyici tanımlıyoruz. Önceden hesaplanmış verilere ihtiyaç yoksa, aslında *değerler için varsayılan geri dönüş* olan `SamplerTrivial` örnekleyicisi ile uygulanabilir.

Rastgele nesne üretimini `S` türündeki nesnelerden tanımlamak için aşağıdaki yöntem tanımlanmalıdır: `rand(rng::AbstractRNG, sp::Random.SamplerTrivial{S})`. Burada, `sp` basitçe `S` türündeki bir nesneyi sarmalar ve bu nesneye `sp[]` ile erişilebilir. `Die` örneğini devam ettirerek, şimdi `rand(d::Die)` tanımlamak istiyoruz; bu, `d`'nin bir yüzüne karşılık gelen bir `Int` üretmelidir:

```jldoctest Die; setup = :(Random.seed!(1))
julia> Random.rand(rng::AbstractRNG, d::Random.SamplerTrivial{Die}) = rand(rng, 1:d[].nsides);

julia> rand(Die(4))
1

julia> rand(Die(4), 3)
3-element Vector{Any}:
 2
 3
 3
```

Verilen bir koleksiyon türü `S` için, `rand(::S)` tanımlıysa, `eltype(S)` türünde bir nesne üretileceği varsayılmaktadır. Son örnekte, bir `Vector{Any}` üretilmiştir; bunun nedeni `eltype(Die) == Any` olmasıdır. Çözüm, `Base.eltype(::Type{Die}) = Int` tanımlamaktır.

#### Generating values for an `AbstractFloat` type

`AbstractFloat` türleri özel durumlar olarak ele alınır, çünkü varsayılan olarak rastgele değerler tüm tür alanında üretilmez, bunun yerine `[0,1)` aralığında üretilir. Aşağıdaki yöntem `T <: AbstractFloat` için uygulanmalıdır: `Random.rand(::AbstractRNG, ::Random.SamplerTrivial{Random.CloseOpen01{T}})`

#### An optimized sampler with pre-computed data

Bir ayrık dağılımı düşünün; burada `1:n` sayıları, toplamı bir olan belirli olasılıklarla çekilir. Bu dağılımdan birçok değer gerektiğinde, en hızlı yöntem [alias table](https://en.wikipedia.org/wiki/Alias_method) kullanmaktır. Böyle bir tablo oluşturma algoritmasını burada sağlamıyoruz, ancak bunun yerine `make_alias_table(probabilities)` fonksiyonunun mevcut olduğunu varsayalım ve `draw_number(rng, alias_table)` fonksiyonu kullanılarak ondan rastgele bir sayı çekilebilir.

Dağılımın şu şekilde tanımlandığını varsayalım:

```julia
struct DiscreteDistribution{V <: AbstractVector}
    probabilities::V
end
```

ve ve *her zaman* bir takma ad tablosu oluşturmak istediğimizi, gereken değer sayısından bağımsız olarak (bunu aşağıda özelleştirmeyi öğreniyoruz). Yöntemler

```julia
Random.eltype(::Type{<:DiscreteDistribution}) = Int

function Random.Sampler(::Type{<:AbstractRNG}, distribution::DiscreteDistribution, ::Repetition)
    SamplerSimple(distribution, make_alias_table(distribution.probabilities))
end
```

önceden hesaplanmış verilerle bir örnekleyici döndürmek için tanımlanmalıdır, o zaman

```julia
function rand(rng::AbstractRNG, sp::SamplerSimple{<:DiscreteDistribution})
    draw_number(rng, sp.data)
end
```

değerleri çizmek için kullanılacaktır.

#### Custom sampler types

`SamplerSimple` türü, önceden hesaplanmış verilerle çoğu kullanım durumu için yeterlidir. Ancak, özel örnekleyici türlerini nasıl kullanacağınızı göstermek için burada `SamplerSimple`'a benzer bir şey uyguluyoruz.

`Die` örneğimize geri dönersek: `rand(::Die)` bir aralıktan rastgele üretim kullanır, bu nedenle bu optimizasyon için bir fırsat vardır. Özel örnekleyicimize `SamplerDie` adını veriyoruz.

```julia
import Random: Sampler, rand

struct SamplerDie <: Sampler{Int} # generates values of type Int
    die::Die
    sp::Sampler{Int} # this is an abstract type, so this could be improved
end

Sampler(RNG::Type{<:AbstractRNG}, die::Die, r::Random.Repetition) =
    SamplerDie(die, Sampler(RNG, 1:die.nsides, r))
# the `r` parameter will be explained later on

rand(rng::AbstractRNG, sp::SamplerDie) = rand(rng, sp.sp)
```

Artık `sp = Sampler(rng, die)` ile bir örnekleyici almak ve `rng` ile ilgili herhangi bir `rand` çağrısında `die` yerine `sp` kullanmak mümkün. Yukarıdaki basit örnekte, `die`'nin `SamplerDie` içinde saklanmasına gerek yoktur, ancak pratikte bu genellikle böyle olur.

Tabii ki, bu desen o kadar sık ki, yukarıda kullanılan yardımcı tür, yani `Random.SamplerSimple`, mevcut ve `SamplerDie` tanımını yapmamıza gerek kalmıyor: ayrıştırmamızı şu şekilde uygulayabilirdik:

```julia
Sampler(RNG::Type{<:AbstractRNG}, die::Die, r::Random.Repetition) =
    SamplerSimple(die, Sampler(RNG, 1:die.nsides, r))

rand(rng::AbstractRNG, sp::SamplerSimple{Die}) = rand(rng, sp.data)
```

Burada, `sp.data`, `SamplerSimple` yapıcısına yapılan çağrıda ikinci parametreyi ifade eder (bu durumda `Sampler(rng, 1:die.nsides, r)` ile eşittir), `Die` nesnesine ise `sp[]` aracılığıyla erişilebilir.

`SamplerDie` gibi, herhangi bir özel örnekleyici `Sampler{T}` alt türü olmalıdır; burada `T`, üretilen değerlerin türüdür. `SamplerSimple(x, data) isa Sampler{eltype(x)}` olduğu için, bu `SamplerSimple`'a ilk argümanın ne olabileceğini kısıtlar (ilk argüman olarak `SamplerSimple`'ı kullanmanız önerilir; burada `x`, bir `Sampler` yöntemi tanımlarken basitçe iletilir). Benzer şekilde, `SamplerTrivial(x) isa Sampler{eltype(x)}`.

Başka bir yardımcı tür, `Random.SamplerTag`, diğer durumlar için mevcut, ancak dahili API olarak kabul edilir ve uygun bir deprekasyon olmadan herhangi bir zamanda bozulabilir.

#### Using distinct algorithms for scalar or array generation

Bazı durumlarda, yalnızca birkaç değer üretmek isteyip istemediğiniz veya büyük sayıda değer üretmek isteyip istemediğiniz, algoritma seçiminde etkili olacaktır. Bu, `Sampler` yapıcısının üçüncü parametresi ile ele alınır. İki yardımcı tür tanımladığımızı varsayalım, `Die` için, `SamplerDie1` yalnızca birkaç rastgele değer üretmek için kullanılacak ve `SamplerDieMany` ise birçok değer için kullanılacak. Bu türleri aşağıdaki gibi kullanabiliriz:

```julia
Sampler(RNG::Type{<:AbstractRNG}, die::Die, ::Val{1}) = SamplerDie1(...)
Sampler(RNG::Type{<:AbstractRNG}, die::Die, ::Val{Inf}) = SamplerDieMany(...)
```

Elbette, `rand` bu türler üzerinde de tanımlanmalıdır (yani `rand(::AbstractRNG, ::SamplerDie1)` ve `rand(::AbstractRNG, ::SamplerDieMany)`). Her zamanki gibi, özel türler gerekli değilse `SamplerTrivial` ve `SamplerSimple` kullanılabilir.

Not: `Sampler(rng, x)` sadece `Sampler(rng, x, Val(Inf))` için bir kısayoldur ve `Random.Repetition` `Union{Val{1}, Val{Inf}}` için bir takma addır.

### Creating new generators

API henüz net bir şekilde tanımlanmamış, ancak genel bir kural olarak:

1. herhangi bir `rand` yöntemi "temel" türler (`isbitstype` tam sayılar ve `Base` içindeki kayan nokta türleri) üretiyorsa, bunlar bu özel RNG için tanımlanmalıdır, eğer gerekiyorsa;
2. diğer belgelenmiş `rand` yöntemleri bir `AbstractRNG` kabul ediyorsa kutudan çıktığı gibi çalışmalıdır, (1) numaralı maddeden hangi yöntemlerin kullanıldığı uygulanmışsa), ancak elbette bu RNG için optimizasyon alanı varsa özelleştirilebilir;
3. `copy` için pseudo-RNG'ler, çağrıldığında aynı şekilde orijinal ile aynı rastgele diziyi üreten bağımsız bir kopya döndürmelidir. Bu mümkün olmadığında (örneğin, donanım tabanlı RNG'ler), `copy` uygulanmamalıdır.

Concerning 1), a `rand` method may happen to work automatically, but it's not officially supported and may break without warnings in a subsequent release.

Yeni bir `rand` metodunu varsayımsal bir `MyRNG` jeneratörü için tanımlamak ve bir değer spesifikasyonu `s` (örneğin `s == Int` veya `s == 1:10`) tanımlamak için, `S==typeof(s)` veya `S==Type{s}` ise `s` bir türse, daha önce gördüğümüz aynı iki metod tanımlanmalıdır:

1. `Sampler(::Type{MyRNG}, ::S, ::Repetition)`, bu `SamplerS` türünde bir nesne döndürür.
2. `rand(rng::MyRNG, sp::SamplerS)`

`Sampler(rng::AbstractRNG, ::S, ::Repetition)` zaten `Random` modülünde tanımlı olabilir. Bu durumda, pratikte adım 1)'i atlamak mümkün olacaktır (eğer bu belirli RNG türü için üretimi özelleştirmek isteniyorsa), ancak ilgili `SamplerS` türü içsel bir detay olarak kabul edilir ve uyarı olmaksızın değiştirilebilir.

#### Specializing array generation

Bazı durumlarda, belirli bir RNG türü için, rastgele değerler dizisi oluşturmak, daha önce açıklanan ayrıştırma tekniğini kullanmaktan daha verimli olabilir. Bu, örneğin, rastgele değerleri bir diziye yerel olarak yazan `MersenneTwister` için geçerlidir.

`MyRNG` için bu özel durumu ve `s` spesifikasyonunu uygulamak için, `S` türünde elemanlar üreten aşağıdaki yöntem tanımlanabilir: `rand!(rng::MyRNG, a::AbstractArray{S}, ::SamplerS)`, burada `SamplerS`, `Sampler(MyRNG, s, Val(Inf))` tarafından döndürülen örnekleyicinin türüdür. `AbstractArray` yerine, işlevselliği yalnızca bir alt tür için uygulamak mümkündür, örneğin `Array{S}`. `rand`'ın değiştirici olmayan dizi yöntemi, bu özel durumu otomatik olarak dahili olarak çağıracaktır.

```@meta
DocTestSetup = nothing
```

# Reproducibility

RNG parametreleri belirli bir tohum ile başlatıldığında, programınızı birden fazla kez çalıştırdığınızda aynı sahte rastgele sayı dizisini yeniden üretebilirsiniz. Ancak, Julia'nın küçük bir sürümü (örneğin 1.3'ten 1.4'e) belirli bir tohumdan üretilen sahte rastgele sayı dizisini *değiştirebilir*, özellikle `MersenneTwister` kullanılıyorsa. (Düşük seviyeli bir fonksiyonun ürettiği dizinin değişmemesi durumunda bile, [`rand`](@ref) gibi, daha yüksek seviyeli fonksiyonların çıktısı [`randsubseq`](@ref) algoritma güncellemeleri nedeniyle değişebilir.) Gerekçe: sahte rastgele akışların asla değişmeyeceğini garanti etmek, birçok algoritmik iyileştirmeyi engeller.

Eğer rastgele verilerin tam yeniden üretilebilirliğini garanti etmek istiyorsanız, verileri *kaydetmek* (örneğin, bir bilimsel yayında ek bir ek olarak) tavsiye edilir. (Ayrıca, özellikle bit yeniden üretilebilirliğine ihtiyaç duyuyorsanız, belirli bir Julia sürümünü ve paket manifestosunu da belirtebilirsiniz.)

Yazılım testleri, *belirli* "rastgele" verilere dayanıyorsa, genellikle verileri kaydetmeli, test koduna gömmeli veya [StableRNGs.jl](https://github.com/JuliaRandom/StableRNGs.jl) gibi üçüncü taraf paketler kullanmalıdır. Öte yandan, *çoğu* rastgele veri için geçmesi gereken testler (örneğin, rastgele bir matris `A = randn(n,n)` için `A \ (A*x) ≈ x` test etme) çok olasılıksız veriler nedeniyle testin birçok kez çalıştırılmasının başarısızlıkla karşılaşmamasını sağlamak için sabit bir tohum ile bir RNG kullanabilir.

İstatistiksel *dağılım*, rastgele örneklerin alındığı *aynı* minor Julia sürümleri arasında garanti edilmektedir.
