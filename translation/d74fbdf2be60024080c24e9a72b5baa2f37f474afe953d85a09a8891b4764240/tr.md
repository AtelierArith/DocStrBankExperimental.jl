# SubArrays

Julia'nın `SubArray` türü, bir ana [`AbstractArray`](@ref)'nın "görünümünü" kodlayan bir konteynerdir. Bu sayfa, `SubArray`'lerin bazı tasarım ilkelerini ve uygulamalarını belgeler.

Birincil tasarım hedeflerinden biri, hem [`IndexLinear`](@ref) hem de [`IndexCartesian`](@ref) dizilerinin görünümleri için yüksek performans sağlamaktır. Ayrıca, `IndexLinear` dizilerinin görünümleri mümkün olduğunca `IndexLinear` olmalıdır.

## Index replacement

2d dilimlerini 3d bir diziden oluşturmayı düşünün:

```@meta
DocTestSetup = :(import Random; Random.seed!(1234))
```

```jldoctest subarray
julia> A = rand(2,3,4);

julia> S1 = view(A, :, 1, 2:3)
2×2 view(::Array{Float64, 3}, :, 1, 2:3) with eltype Float64:
 0.839622  0.711389
 0.967143  0.103929

julia> S2 = view(A, 1, :, 2:3)
3×2 view(::Array{Float64, 3}, 1, :, 2:3) with eltype Float64:
 0.839622  0.711389
 0.789764  0.806704
 0.566704  0.962715
```

```@meta
DocTestSetup = nothing
```

`view` "singleton" boyutları (bir `Int` ile belirtilen) kaldırır, bu nedenle hem `S1` hem de `S2` iki boyutlu `SubArray`'lerdir. Sonuç olarak, bunları indekslemenin doğal yolu `S1[i,j]` şeklindedir. Ana dizi `A`'dan değeri çıkarmak için doğal yaklaşım, `S1[i,j]`'yi `A[i,1,(2:3)[j]]` ile ve `S2[i,j]`'yi `A[1,i,(2:3)[j]]` ile değiştirmektir.

Alt dizaynının ana özelliği, bu indeks değişiminin herhangi bir çalışma zamanı yükü olmadan gerçekleştirilebilmesidir.

## SubArray design

### Type parameters and fields

Benimsenen strateji öncelikle türün tanımında ifade edilmektedir:

```julia
struct SubArray{T,N,P,I,L} <: AbstractArray{T,N}
    parent::P
    indices::I
    offset1::Int       # for linear indexing and pointer, only valid when L==true
    stride1::Int       # used only for linear indexing
    ...
end
```

`SubArray` 5 tür parametresine sahiptir. İlk ikisi standart eleman türü ve boyutsallıktır. Üçüncüsü, üst `AbstractArray` türüdür. En çok kullanılan dördüncü parametre, her boyut için indeks türlerinin bir `Tuple`'ıdır. Sonuncusu, `L`, yalnızca dağıtım için bir kolaylık olarak sağlanır; hızlı lineer indekslemeyi destekleyip desteklemediğini temsil eden bir boole'dir. Daha sonra bununla ilgili daha fazla bilgi.

Eğer yukarıdaki örneğimizde `A` bir `Array{Float64, 3}` ise, yukarıdaki `S1` durumu bir `SubArray{Float64,2,Array{Float64,3},Tuple{Base.Slice{Base.OneTo{Int64}},Int64,UnitRange{Int64}},false}` olacaktır. Özellikle, `S1`'i oluşturmak için kullanılan indekslerin türlerini saklayan tuple parametresine dikkat edin. Aynı şekilde,

```jldoctest subarray
julia> S1.indices
(Base.Slice(Base.OneTo(2)), 1, 2:3)
```

Bu değerleri depolamak, indeks değiştirmeye olanak tanır ve türlerin parametreler olarak kodlanması, verimli algoritmalara yönlendirme yapmayı sağlar.

### Index translation

İndeks çevirisi yapmak, farklı somut `SubArray` türleri için farklı şeyler yapmayı gerektirir. Örneğin, `S1` için `i,j` indekslerini ana dizinin birinci ve üçüncü boyutlarına uygulamak gerekirken, `S2` için bunları ikinci ve üçüncü boyutlara uygulamak gerekir. İndeksleme için en basit yaklaşım, tür analizini çalışma zamanında yapmaktır:

```julia
parentindices = Vector{Any}()
for thisindex in S.indices
    ...
    if isa(thisindex, Int)
        # Don't consume one of the input indices
        push!(parentindices, thisindex)
    elseif isa(thisindex, AbstractVector)
        # Consume an input index
        push!(parentindices, thisindex[inputindex[j]])
        j += 1
    elseif isa(thisindex, AbstractMatrix)
        # Consume two input indices
        push!(parentindices, thisindex[inputindex[j], inputindex[j+1]])
        j += 2
    elseif ...
end
S.parent[parentindices...]
```

Maalesef, bu performans açısından felaket olurdu: her bir öğe erişimi bellek tahsis ederdi ve çok sayıda kötü tiplenmiş kodun çalıştırılmasını içerirdi.

Daha iyi yaklaşım, her tür saklanan indeksle başa çıkmak için belirli yöntemlere yönlendirmektir. `reindex` işlevi de budur: ilk saklanan indeksin türüne göre yönlendirir ve uygun sayıda girdi indeksini tüketir, ardından kalan indeksler üzerinde yineleme yapar. `S1` durumunda, bu genişler:

```julia
Base.reindex(S1, S1.indices, (i, j)) == (i, S1.indices[2], S1.indices[3][j])
```

herhangi bir indeks çifti `(i,j)` için (aşağıda belirtilen [`CartesianIndex`](@ref) ve dizileri hariç).

Bu, bir `SubArray`'nin çekirdeğidir; indeksleme yöntemleri bu indeks çevirimi için `reindex`'e dayanır. Ancak bazen dolaylı yoldan kaçınabiliriz ve bunu daha da hızlı hale getirebiliriz.

### Linear indexing

Lineer indeksleme, tüm dizinin ardışık elemanları ayıran tek bir adım ile bir ofsetten başlayarak verimli bir şekilde uygulanabilir. Bu, bu değerleri önceden hesaplayabileceğimiz ve lineer indekslemeyi basit bir toplama ve çarpma olarak temsil edebileceğimiz anlamına gelir; böylece `reindex`'in dolaylılığını ve (daha da önemlisi) kartezyen koordinatların yavaş hesaplanmasını tamamen önleyebiliriz.

`SubArray` türleri için, verimli doğrusal indekslemenin mevcutlığı tamamen indekslerin türlerine dayanır ve ana dizinin boyutu gibi değerlere bağlı değildir. Belirli bir indeks kümesinin hızlı doğrusal indekslemeyi destekleyip desteklemediğini, dahili `Base.viewindexing` fonksiyonu ile sorabilirsiniz:

```jldoctest subarray
julia> Base.viewindexing(S1.indices)
IndexCartesian()

julia> Base.viewindexing(S2.indices)
IndexLinear()
```

Bu, `SubArray`'nın inşası sırasında hesaplanır ve hızlı doğrusal indeksleme desteğini kodlayan bir boolean olarak `L` tür parametresinde saklanır. Kesinlikle gerekli olmamakla birlikte, `SubArray{T,N,A,I,true}` üzerinde doğrudan dağıtım tanımlayabilmemizi sağlar.

Bu hesaplama çalışma zamanı değerlerine bağlı olmadığından, adımın tesadüfen uniform olduğu bazı durumları atlayabilir:

```jldoctest
julia> A = reshape(1:4*2, 4, 2)
4×2 reshape(::UnitRange{Int64}, 4, 2) with eltype Int64:
 1  5
 2  6
 3  7
 4  8

julia> diff(A[2:2:4,:][:])
3-element Vector{Int64}:
 2
 2
 2
```

`view(A, 2:2:4, :)` olarak oluşturulan bir görünüm, uniform stride'a sahip olduğundan, doğrusal indeksleme gerçekten de verimli bir şekilde gerçekleştirilebilir. Ancak, bu durumda başarı dizinin boyutuna bağlıdır: eğer ilk boyut tek olsaydı,

```jldoctest
julia> A = reshape(1:5*2, 5, 2)
5×2 reshape(::UnitRange{Int64}, 5, 2) with eltype Int64:
 1   6
 2   7
 3   8
 4   9
 5  10

julia> diff(A[2:2:4,:][:])
3-element Vector{Int64}:
 2
 3
 2
```

o zaman `A[2:2:4,:]` uniform adım aralığına sahip değildir, bu nedenle verimli doğrusal indeksleme garantisi veremeyiz. Bu kararı tamamen `SubArray` parametrelerinde kodlanmış türlere dayandırmamız gerektiğinden, `S = view(A, 2:2:4, :)` verimli doğrusal indekslemeyi uygulayamaz.

### A few details

  * `Base.reindex` fonksiyonunun girdi indekslerinin türlerine kayıtsız olduğunu unutmayın; yalnızca saklanan indekslerin nasıl ve nerede yeniden indekslenmesi gerektiğini belirler. Bu, yalnızca tam sayı indekslerini desteklemekle kalmaz, aynı zamanda skalar olmayan indekslemeyi de destekler. Bu, görünümün görünümünün iki düzey dolaylılığa ihtiyaç duymadığı anlamına gelir; bunlar, yalnızca orijinal ana diziye indeksleri yeniden hesaplayabilir!
  * Umarım şimdi destekleyen dilimlerin, `N` parametresiyle verilen boyutun, ana dizinin boyutuyla veya `indices` demetinin uzunluğuyla eşit olmayabileceği oldukça net olmuştur. Kullanıcı tarafından sağlanan indekslerin de mutlaka `indices` demetindeki girişlerle örtüşmesi gerekmez (örneğin, ikinci kullanıcı tarafından sağlanan indeks ana dizinin üçüncü boyutuna karşılık gelebilir ve `indices` demetindeki üçüncü elemana denk gelebilir).

    Daha az belirgin olan şey, saklanan üst dizi boyutunun `indices` demetindeki etkili indeks sayısına eşit olması gerektiğidir. İşte bazı örnekler:

    ```julia
    A = reshape(1:35, 5, 7) # A 2d parent Array
    S = view(A, 2:7)         # A 1d view created by linear indexing
    S = view(A, :, :, 1:1)   # Appending extra indices is supported
    ```

    Naif olarak, `S.parent = A` ve `S.indices = (:,:,1:1)` ayarlayabileceğinizi düşünebilirsiniz, ancak bunu desteklemek yeniden indeksleme sürecini dramatik bir şekilde karmaşıklaştırır, özellikle de görünümler için. Saklanan indekslerin türlerine göre dağıtım yapmanızın yanı sıra, belirli bir indeksin son indeks olup olmadığını incelemeniz ve kalan saklanan indeksleri "birleştirmeniz" gerekir. Bu kolay bir iş değil ve daha da kötüsü: bu, doğrusal indekslemeye dolaylı olarak bağlı olduğu için yavaştır.

    Neyse ki, bu tam olarak `ReshapedArray`'ın gerçekleştirdiği hesaplamadır ve mümkünse bunu lineer olarak yapar. Sonuç olarak, `view`, ana dizinin verilen indeksler için uygun boyutta olmasını sağlamak amacıyla gerekirse onu yeniden şekillendirir. İçteki `SubArray` yapıcı, bu değişmezliğin sağlandığından emin olur.
  * [`CartesianIndex`](@ref) ve dizileri, `reindex` şemasına kötü bir engel çıkarır. `reindex`'in, saklanan indekslerin türüne göre kaç tane geçirilen indeksin kullanılacağını ve bunların nereye gideceğini belirlemek için basitçe dağıtım yaptığını hatırlayın. Ancak `CartesianIndex` ile, geçirilen argümanların sayısı ile bunların indekslediği boyutlar arasında artık birebir bir ilişki yoktur. Yukarıdaki `Base.reindex(S1, S1.indices, (i, j))` örneğine dönersek, `i, j = CartesianIndex(), CartesianIndex(2,1)` için genişlemenin yanlış olduğunu görebilirsiniz. Tamamen `CartesianIndex()`'i *atlamalı* ve şunu döndürmelidir:

    ```julia
    (CartesianIndex(2,1)[1], S1.indices[2], S1.indices[3][CartesianIndex(2,1)[2]])
    ```

    Bunun yerine, ama, şunu alıyoruz:

    ```julia
    (CartesianIndex(), S1.indices[2], S1.indices[3][CartesianIndex(2,1)])
    ```

    Bunu doğru yapmak, tüm boyut kombinasyonları boyunca hem saklanan hem de geçirilen indeksler üzerinde *birleşik* dağıtım gerektirecektir ve bu da yönetilemez bir şekilde olacaktır. Bu nedenle, `reindex` asla `CartesianIndex` indeksleri ile çağrılmamalıdır. Neyse ki, skalar durum, `CartesianIndex` argümanlarını düz tam sayılara dönüştürerek kolayca işlenebilir. Ancak, `CartesianIndex` dizileri bu kadar kolay bir şekilde ortogonal parçalara ayrılamaz. `reindex` kullanmaya çalışmadan önce, `view`, argüman listesinde `CartesianIndex` dizileri olmadığından emin olmalıdır. Eğer varsa, `reindex` hesaplamasını tamamen atlayarak iki seviyeli bir `SubArray` oluşturarak "topu taca atabilir".
