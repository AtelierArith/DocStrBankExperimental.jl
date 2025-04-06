```
begin
```

`begin...end` bir kod bloğunu belirtir.

```julia
begin
    println("Merhaba, ")
    println("Dünya!")
end
```

Genellikle `begin` gerekli olmayacaktır, çünkü [`function`](@ref) ve [`let`](@ref) gibi anahtar kelimeler, kod bloklarını örtük olarak başlatır. Ayrıca bkz. [`;`](@ref).

`begin` ayrıca bir koleksiyonun ilk indeksini veya bir dizinin ilk indeksini temsil etmek için dizinleme sırasında da kullanılabilir. Örneğin, `a[begin]` bir dizi `a`nın ilk elemanıdır.

!!! compat "Julia 1.4"
    Dizin olarak `begin` kullanımı Julia 1.4 veya daha yenisini gerektirir.


# Örnekler

```jldoctest
julia> A = [1 2; 3 4]
2×2 Array{Int64,2}:
 1  2
 3  4

julia> A[begin, :]
2-element Array{Int64,1}:
 1
 2
```
