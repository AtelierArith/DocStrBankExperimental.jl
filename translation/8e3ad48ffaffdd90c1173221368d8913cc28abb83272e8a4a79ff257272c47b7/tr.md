```
benzer(array, [element_type=eltype(array)], [dims=size(array)])
```

Verilen kaynak diziye dayalı olarak, belirtilen eleman türü ve boyut ile başlatılmamış bir değişken dizi oluşturur. İkinci ve üçüncü argümanlar isteğe bağlıdır ve varsayılan olarak verilen dizinin `eltype` ve `size` değerlerine ayarlanır. Boyutlar, ya tek bir demet argümanı olarak ya da bir dizi tam sayı argümanı olarak belirtilebilir.

Özel AbstractArray alt türleri, verilen eleman türü ve boyut için en uygun dizi türünü döndürmeyi seçebilir. Bu yöntemi özelleştirmezlerse, varsayılan olarak `Array{element_type}(undef, dims...)` döner.

Örneğin, `benzer(1:10, 1, 4)` başlatılmamış bir `Array{Int,2}` döner çünkü aralıklar ne değişkendir ne de 2 boyut destekler:

```julia-repl
julia> benzer(1:10, 1, 4)
1×4 Matrix{Int64}:
 4419743872  4374413872  4419743888  0
```

Tersine, `benzer(trues(10,10), 2)` iki elemanlı başlatılmamış bir `BitVector` döner çünkü `BitArray`'ler hem değişkendir hem de 1 boyutlu dizileri destekleyebilir:

```julia-repl
julia> benzer(trues(10,10), 2)
2-element BitVector:
 0
 0
```

Ancak, `BitArray`'ler yalnızca [`Bool`](@ref) türündeki elemanları depolayabildiğinden, farklı bir eleman türü talep ederseniz, bunun yerine normal bir `Array` oluşturur:

```julia-repl
julia> benzer(falses(10), Float64, 2, 4)
2×4 Matrix{Float64}:
 2.18425e-314  2.18425e-314  2.18425e-314  2.18425e-314
 2.18425e-314  2.18425e-314  2.18425e-314  2.18425e-314
```

Ayrıca bakınız: [`undef`](@ref), [`isassigned`](@ref). ```
