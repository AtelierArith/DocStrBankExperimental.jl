# [Arrays with custom indices](@id man-custom-indices)

Geleneksel olarak, Julia'nın dizileri 1'den başlamak üzere indekslenirken, bazı diğer diller 0'dan numaralandırmaya başlar ve daha başkaları (örneğin, Fortran) keyfi başlangıç indeksleri belirtmenize izin verir. Bir standart belirlemenin (yani, Julia için 1) birçok avantajı olsa da, bazı algoritmalar, `1:size(A,d)` aralığının dışındaki indeksleme yapabildiğinizde önemli ölçüde basitleşir (ve sadece `0:size(A,d)-1` ile de sınırlı değildir). Bu tür hesaplamaları kolaylaştırmak için, Julia keyfi indekslere sahip dizileri destekler.

Bu sayfanın amacı, "Kendi kodumda böyle dizileri desteklemek için ne yapmalıyım?" sorusunu ele almaktır. Öncelikle, en basit durumu ele alalım: Kodunuzun alışılmadık indeksleme ile dizileri asla işlemek zorunda kalmayacağını biliyorsanız, umarım cevap "hiçbir şey"dir. Eski kod, geleneksel diziler üzerinde, Julia'nın dışa aktarılan arayüzlerini kullanıyorsa, esasen herhangi bir değişiklik olmaksızın çalışmalıdır. Kullanıcılarınızın indekslemenin birden başladığı geleneksel dizileri sağlamasını zorunlu kılmanın daha uygun olduğunu düşünüyorsanız, ekleyebilirsiniz

```julia
Base.require_one_based_indexing(arrays...)
```

`arrays...` 1 tabanlı indekslemeyi ihlal eden herhangi bir şeyi kontrol etmek istediğiniz dizi nesnelerinin bir listesidir.

## Generalizing existing code

Bir genel bakış olarak, adımlar şunlardır:

  * Sure! Please provide the Markdown content or text you'd like me to translate.
  * `eachindex(A)` ile `1:length(A)`'yi değiştirin, ya da bazı durumlarda `LinearIndices(A)` kullanın.
  * replace explicit allocations like `Array{Int}(undef, size(B))` with `similar(Array{Int}, axes(B))`

Bunlar aşağıda daha ayrıntılı olarak açıklanmıştır.

### Things to watch out for

Çünkü alışılmadık dizinleme, tüm dizilerin 1'den başladığına dair birçok kişinin varsayımlarını bozar, bu tür dizilerin kullanılmasının hataları tetikleme olasılığı her zaman vardır. En sinir bozucu hatalar, yanlış sonuçlar veya segfault'lar (Julia'nın toplam çöküşleri) olacaktır. Örneğin, aşağıdaki fonksiyonu düşünün:

```julia
function mycopy!(dest::AbstractVector, src::AbstractVector)
    length(dest) == length(src) || throw(DimensionMismatch("vectors must match"))
    # OK, now we're safe to use @inbounds, right? (not anymore!)
    for i = 1:length(src)
        @inbounds dest[i] = src[i]
    end
    dest
end
```

Bu kod, vektörlerin 1'den indekslendiğini varsayıyor; eğer `dest`, `src`'den farklı bir indeksten başlıyorsa, bu kodun bir segfault tetikleme olasılığı vardır. (Eğer segfault alıyorsanız, nedenini bulmaya yardımcı olmak için julia'yı `--check-bounds=yes` seçeneğiyle çalıştırmayı deneyin.)

### Using `axes` for bounds checks and loop iteration

`axes(A)` (A'nın `size(A)`'ya benzer) `A`'nın her boyutu boyunca geçerli indekslerin aralığını belirten bir `AbstractUnitRange{<:Integer}` nesneleri tuple'ı döndürür. `A` alışılmadık bir indeksleme yapısına sahipse, aralıklar 1'den başlamayabilir. Sadece belirli bir boyut `d` için aralığı istiyorsanız, `axes(A, d)` kullanabilirsiniz.

Base, `OneTo` özel bir aralık türü uygular; burada `OneTo(n)`, `1:n` ile aynı anlama gelir, ancak alt indeksin 1 olduğunu garanti eden bir biçimde (tip sistemi aracılığıyla). Herhangi bir yeni [`AbstractArray`](@ref) türü için, bu `axes` tarafından döndürülen varsayılan değerdir ve bu, bu dizi türünün "geleneksel" 1 tabanlı indeksleme kullandığını gösterir.

Sınır kontrolü için, bazen bu tür testleri basitleştirebilecek `checkbounds` ve `checkindex` adlı özel işlevlerin olduğunu unutmayın.

### Linear indexing (`LinearIndices`)

Bazı algoritmalar, `A[i]` şeklinde tek bir lineer indeks cinsinden en uygun (veya verimli) bir şekilde yazılabilir, hatta `A` çok boyutlu olsa bile. Dizinin yerel indekslerinden bağımsız olarak, lineer indeksler her zaman `1:length(A)` aralığındadır. Ancak, bu durum bir boyutlu diziler için bir belirsizlik yaratır (diğer adıyla, [`AbstractVector`](@ref)): `v[i]` ifadesi lineer indeksleme mi yoksa dizinin yerel indeksleri ile Kartezyen indeksleme mi anlamına geliyor?

Bu nedenle, en iyi seçeneğiniz `eachindex(A)` ile diziyi yinelemek olabilir veya, eğer dizinlerin ardışık tam sayılar olmasını istiyorsanız, `LinearIndices(A)` çağrısını yaparak dizin aralığını alabilirsiniz. Bu, A bir AbstractVector ise `axes(A, 1)` döndürecektir ve aksi takdirde `1:length(A)` ile eşdeğer olacaktır.

Bu tanıma göre, 1 boyutlu diziler her zaman dizinin yerel indeksleri ile Kartezyen indeksleme kullanır. Bunu pekiştirmek için, indeks dönüşüm fonksiyonlarının, şeklin alışılmadık indeksleme ile 1 boyutlu bir dizi gösterdiğinde (yani, `Tuple{UnitRange}` yerine `OneTo`'dan oluşan bir tuple olduğunda) bir hata fırlatacağını belirtmek önemlidir. Alışılmış indekslemeye sahip diziler için, bu fonksiyonlar her zamanki gibi çalışmaya devam eder.

`axes` ve `LinearIndices` kullanarak, `mycopy!` fonksiyonunu şu şekilde yeniden yazabilirsiniz:

```julia
function mycopy!(dest::AbstractVector, src::AbstractVector)
    axes(dest) == axes(src) || throw(DimensionMismatch("vectors must match"))
    for i in LinearIndices(src)
        @inbounds dest[i] = src[i]
    end
    dest
end
```

### Allocating storage using generalizations of `similar`

Depolama genellikle `Array{Int}(undef, dims)` veya `similar(A, args...)` ile tahsis edilir. Sonuç, başka bir dizinin indeksleriyle eşleşmesi gerektiğinde, bu her zaman yeterli olmayabilir. Bu tür desenler için genel bir alternatif, `similar(storagetype, shape)` kullanmaktır. `storagetype`, istediğiniz temel "geleneksel" davranışın türünü belirtir, örneğin `Array{Int}` veya `BitArray` veya hatta `dims->zeros(Float32, dims)` (bu, tamamen sıfırdan oluşan bir dizi tahsis eder). `shape`, sonucu kullanmak istediğiniz indeksleri belirten bir [`Integer`](@ref) veya `AbstractUnitRange` değerleri demetidir. A'nın indeksleriyle eşleşen tamamen sıfırdan oluşan bir dizi üretmenin pratik bir yolu, basitçe `zeros(A)` kullanmaktır.

Birkaç açık örnek üzerinden geçelim. İlk olarak, eğer `A` geleneksel indekslere sahipse, o zaman `similar(Array{Int}, axes(A))` `Array{Int}(undef, size(A))` çağrısını yapacak ve dolayısıyla bir dizi döndürecektir. Eğer `A` alışılmadık indeksleme ile bir `AbstractArray` türü ise, o zaman `similar(Array{Int}, axes(A))` `A` ile eşleşen bir şekle (indeksler dahil) sahip olan ve "Array{Int}" gibi davranan bir şey döndürmelidir. (En bariz uygulama, `Array{Int}(undef, size(A))` tahsis etmek ve ardından indeksleri kaydıran bir tür içinde "sarmalamak" olacaktır.)

Ayrıca, `similar(Array{Int}, (axes(A, 2),))` ifadesinin `A`'nın sütunlarının indeksleriyle eşleşen bir `AbstractVector{Int}` (yani, 1 boyutlu dizi) tahsis edeceğini de unutmayın.

## Writing custom array types with non-1 indexing

Çoğu tanımlamanız gereken yöntem, herhangi bir `AbstractArray` türü için standarttır, bkz. [Abstract Arrays](@ref man-interface-array). Bu sayfa, alışılmadık indeksleme tanımlamak için gereken adımlara odaklanmaktadır.

### Custom `AbstractUnitRange` types

Eğer 1'den başlamayan bir dizi türü yazıyorsanız, `axes`'i özelleştirmek isteyeceksiniz, böylece bir `UnitRange` veya (belki daha iyi) özel bir `AbstractUnitRange` döndürür. Özel bir türün avantajı, `similar` gibi fonksiyonlar için tahsis türünü "sezdiriyor" olmasıdır. Eğer indekslemenin 0'dan başlayacağı bir dizi türü yazıyorsak, muhtemelen yeni bir `AbstractUnitRange`, `ZeroRange` oluşturarak başlamak isteyeceğiz; burada `ZeroRange(n)`, `0:n-1` ile eşdeğerdir.

Genel olarak, paketinizden `ZeroRange`'i *ihtimalle* dışa aktarmamalısınız: kendi `ZeroRange`'lerini uygulayan başka paketler olabilir ve birden fazla farklı `ZeroRange` türüne sahip olmak (belki de sezgisel olarak ters) bir avantajdır: `ModuleA.ZeroRange`, `similar`'ın bir `ModuleA.ZeroArray` oluşturması gerektiğini belirtirken, `ModuleB.ZeroRange`, bir `ModuleB.ZeroArray` türünü belirtir. Bu tasarım, birçok farklı özel dizi türü arasında huzurlu bir varoluşu sağlar.

Not edin ki Julia paketi [CustomUnitRanges.jl](https://github.com/JuliaArrays/CustomUnitRanges.jl) bazen kendi `ZeroRange` türünüzü yazma ihtiyacını ortadan kaldırmak için kullanılabilir.

### Specializing `axes`

Bir `AbstractUnitRange` türünüz olduğunda, ardından `axes`'i özelleştirin:

```julia
Base.axes(A::ZeroArray) = map(n->ZeroRange(n), A.size)
```

burada `ZeroArray`'in `size` adında bir alanı olduğunu hayal ediyoruz (bunu uygulamanın başka yolları da olabilirdi).

Bazı durumlarda, `axes(A, d)` için yedek tanım:

```julia
axes(A::AbstractArray{T,N}, d) where {T,N} = d <= N ? axes(A)[d] : OneTo(1)
```

istediğiniz şey olmayabilir: `d > ndims(A)` olduğunda `OneTo(1)` dışında bir şey döndürmek için onu özelleştirmeniz gerekebilir. Benzer şekilde, `Base` içinde `ndims(A) > 0` olup olmadığını (çalışma zamanında) kontrol etmeyen `axes1` adlı özel bir fonksiyon vardır; bu, `axes(A, 1)` ile eşdeğerdir. (Bu tamamen bir performans optimizasyonudur.) Şu şekilde tanımlanmıştır:

```julia
axes1(A::AbstractArray{T,0}) where {T} = OneTo(1)
axes1(A::AbstractArray) = axes(A)[1]
```

Eğer bunlardan ilki (sıfır boyutlu durum) özel dizi türünüz için sorunluysa, uygun şekilde özelleştirdiğinizden emin olun.

### Specializing `similar`

Verilen özel `ZeroRange` türünüz için, `benzer` için aşağıdaki iki özel durumu da eklemelisiniz:

```julia
function Base.similar(A::AbstractArray, T::Type, shape::Tuple{ZeroRange,Vararg{ZeroRange}})
    # body
end

function Base.similar(f::Union{Function,DataType}, shape::Tuple{ZeroRange,Vararg{ZeroRange}})
    # body
end
```

Her ikisi de özel dizi türünüzü ayırmalıdır.

### Specializing `reshape`

İsteğe bağlı olarak, bir yöntem tanımlayın

```
Base.reshape(A::AbstractArray, shape::Tuple{ZeroRange,Vararg{ZeroRange}}) = ...
```

ve ve `reshape` bir diziyi, böylece sonucun özel indekslere sahip olmasını sağlayabilirsiniz.

### For objects that mimic AbstractArray but are not subtypes

`has_offset_axes`, nesneler üzerinde çağırdığınızda `axes` tanımlı olmasına bağlıdır. Eğer nesneniz için bir `axes` yöntemi tanımlamıyorsanız, bir yöntem tanımlamayı düşünün.

```julia
Base.has_offset_axes(obj::MyNon1IndexedArraylikeObject) = true
```

Bu, 1 tabanlı indeksleme varsayımına sahip kodun bir sorunu tespit etmesine ve yanlış sonuçlar döndürmek veya segfault yapmaktansa yardımcı bir hata vermesine olanak tanıyacaktır.

### Catching errors

Eğer yeni dizi türünüz diğer kodlarda hatalara neden oluyorsa, yararlı bir hata ayıklama adımı, `getindex` ve `setindex!` uygulamanızda `@boundscheck`'i yorum satırı haline getirmektir. Bu, her eleman erişiminin sınırları kontrol etmesini sağlar. Ya da, julia'yı `--check-bounds=yes` ile yeniden başlatın.

Bazen, yeni dizi türünüz için `size` ve `length`'i geçici olarak devre dışı bırakmak da faydalı olabilir, çünkü yanlış varsayımlar yapan kodlar genellikle bu işlevleri kullanır.
