# Bounds checking

Modern programlama dilleri gibi, Julia dizilere erişim sırasında program güvenliğini sağlamak için sınır kontrolü kullanır. Sıkı iç döngülerde veya diğer performans kritik durumlarda, çalışma zamanı performansını artırmak için bu sınır kontrollerini atlamak isteyebilirsiniz. Örneğin, vektörleştirilmiş (SIMD) talimatlar yaymak için, döngü gövdeniz dallar içermemeli ve dolayısıyla sınır kontrolleri içermemelidir. Sonuç olarak, Julia, belirli bir blok içinde bu tür sınır kontrollerini atlaması için derleyiciye talimat vermek üzere `@inbounds(...)` makrosunu içerir. Kullanıcı tanımlı dizi türleri, bağlama duyarlı kod seçimi elde etmek için `@boundscheck(...)` makrosunu kullanabilir.

## Eliding bounds checks

`@boundscheck(...)` makrosu, sınır kontrolü yapan kod bloklarını işaretler. Bu tür bloklar `@inbounds(...)` bloğuna yerleştirildiğinde, derleyici bu blokları kaldırabilir. Derleyici, `@boundscheck` bloğunu *yalnızca çağıran işlevin içine yerleştirildiğinde* kaldırır. Örneğin, `sum` yöntemini şu şekilde yazabilirsiniz:

```julia
function sum(A::AbstractArray)
    r = zero(eltype(A))
    for i in eachindex(A)
        @inbounds r += A[i]
    end
    return r
end
```

Özel bir dizi benzeri tür olan `MyArray` ile:

```julia
@inline getindex(A::MyArray, i::Real) = (@boundscheck checkbounds(A, i); A.data[to_index(i)])
```

Sonra `getindex` `sum` içine yerleştirildiğinde, `checkbounds(A, i)` çağrısı atlanacaktır. Fonksiyonunuz birden fazla yerleştirme katmanı içeriyorsa, yalnızca `@boundscheck` blokları en fazla bir yerleştirme katmanı daha derin olanlardan kaldırılır. Bu kural, yığın üzerindeki daha yukarıdaki koddan kaynaklanan istenmeyen program davranışı değişikliklerini önler.

### Caution!

`@inbounds` ile güvenli olmayan işlemleri yanlışlıkla açığa çıkarmak kolaydır. Yukarıdaki örneği yazmaya teşvik edilebilirsiniz.

```julia
function sum(A::AbstractArray)
    r = zero(eltype(A))
    for i in 1:length(A)
        @inbounds r += A[i]
    end
    return r
end
```

Hangi sessizce 1 tabanlı dizinlemeyi varsayıyor ve bu nedenle [`OffsetArrays`](@ref man-custom-indices) ile kullanıldığında güvensiz bellek erişimini açığa çıkarıyor:

```julia-repl
julia> using OffsetArrays

julia> sum(OffsetArray([1, 2, 3], -10))
9164911648 # inconsistent results or segfault
```

Hata kaynağı burada `1:length(A)` iken, `@inbounds` kullanımı bir sınır hatasının sonuçlarını daha az kolay yakalanan ve hata ayıklanan güvensiz bellek erişimine dönüştürür. `@inbounds` kullanan bir yöntemin güvenli olduğunu kanıtlamak genellikle zor veya imkansızdır, bu nedenle performans iyileştirmelerinin faydalarını, özellikle de kamuya açık API'lerde, segfault ve sessiz yanlış davranış riskine karşı tartmak gerekir.

## Propagating inbounds

Kod organizasyonu nedenleriyle `@inbounds` ve `@boundscheck` bildirimleri arasında birden fazla katman istemeniz gereken belirli senaryolar olabilir. Örneğin, varsayılan `getindex` yöntemleri `getindex(A::AbstractArray, i::Real)` çağrısının `getindex(IndexStyle(A), A, i)` çağrısını ve bunun da `_getindex(::IndexLinear, A, i)` çağrısını içerdiği bir zincire sahiptir.

"bir kat iç içe geçiş" kuralını geçersiz kılmak için, bir fonksiyon [`Base.@propagate_inbounds`](@ref) ile işaretlenebilir, böylece bir inbounds bağlamını (veya out of bounds bağlamını) bir ek iç içe geçiş katmanından geçirebilir.

## The bounds checking call hierarchy

Genel hiyerarşi şudur:

  * `checkbounds(A, I...)` çağrılır

      * `checkbounds(Bool, A, I...)` çağrısı yapar

          * `checkbounds_indices(Bool, axes(A), I)` hangi şekilde özyinelemeli olarak çağrılır

              * `her boyut için checkindex`

Burada `A` dizi ve `I` "istenen" indeksleri içerir. `axes(A)` ifadesi `A`'nın "izin verilen" indekslerinin bir demetini döndürür.

`checkbounds(A, I...)` geçersiz indeksler varsa bir hata fırlatır, oysa `checkbounds(Bool, A, I...)` bu durumda `false` döner. `checkbounds_indices`, dizinin `axes` demeti dışındaki bilgileri atar ve saf bir indeksler-arası karşılaştırma yapar: bu, nispeten az sayıda derlenmiş yöntemin büyük bir dizi türü yelpazesine hizmet etmesini sağlar. İndeksler demetler olarak belirtilir ve genellikle bireysel boyutlarla 1-1 biçiminde karşılaştırılır; bu, başka bir önemli işlev olan `checkindex` çağrılarak işlenir: tipik olarak,

```julia
checkbounds_indices(Bool, (IA1, IA...), (I1, I...)) = checkindex(Bool, IA1, I1) &
                                                      checkbounds_indices(Bool, IA, I)
```

`checkindex` tek bir boyutu kontrol eder. Bu işlevlerin tümü, dışa aktarılmamış `checkbounds_indices` dahil, `?` ile erişilebilen dokümantasyon dizelerine sahiptir.

Eğer belirli bir dizi türü için sınır kontrolünü özelleştirmeniz gerekiyorsa, `checkbounds(Bool, A, I...)`'yi özelleştirmelisiniz. Ancak, çoğu durumda, dizi türünüz için yararlı `axes` sağladığınız sürece `checkbounds_indices`'e güvenebilmelisiniz.

Eğer yeni dizin türleriniz varsa, önce bir dizinin belirli bir boyutu için tek bir dizini işleyen `checkindex`'i özelleştirmeyi düşünün. Eğer `CartesianIndex`'e benzer özel bir çok boyutlu dizin türünüz varsa, o zaman `checkbounds_indices`'i özelleştirmeyi düşünmeniz gerekebilir.

Bu hiyerarşi, yöntem belirsizliklerini azaltmak için tasarlanmıştır. `checkbounds`'ı dizi türü üzerinde uzmanlaşmak için bir yer haline getirmeye çalışıyoruz ve indeks türleri üzerinde uzmanlaşmaktan kaçınmaya çalışıyoruz; tersine, `checkindex` yalnızca indeks türü (özellikle son argüman) üzerinde uzmanlaşmak için tasarlanmıştır.

## Emit bounds checks

Julia `--check-bounds={yes|no|auto}` ile her zaman, asla veya `@inbounds` bildirimlerini dikkate alacak şekilde sınır kontrolleri yapacak şekilde başlatılabilir.
