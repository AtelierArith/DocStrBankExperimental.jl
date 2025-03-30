```
Int
```

Sys.WORD_SIZE-bit işaretli tam sayı türü, `Int <: Signed <: Integer <: Real`.

Bu, çoğu tam sayı literali için varsayılan türdür ve `Sys.WORD_SIZE`'a bağlı olarak ya `Int32` ya da `Int64` için bir takma addır. [`length`](@ref) gibi fonksiyonlar tarafından döndürülen türdür ve dizileri indekslemek için standart türdür.

Tam sayıların uyarı olmadan taşma yaptığını unutmayın, bu nedenle `typemax(Int) + 1 < 0` ve `10^19 < 0` doğrudur. Taşmayı önlemek için [`BigInt`](@ref) kullanabilirsiniz. Çok büyük tam sayı literalleri daha geniş bir tür kullanır, örneğin `10_000_000_000_000_000_000 isa Int128`.

Tam sayı bölmesi [`div`](@ref) takma adı `÷` iken, tam sayılar üzerinde [`/`](@ref) kullanmak [`Float64`](@ref) döndürür.

Ayrıca [`Int64`](@ref), [`widen`](@ref), [`typemax`](@ref), [`bitstring`](@ref) ile de bakabilirsiniz.
