```
axes(A, d)
```

Dizi `A` için `d` boyutu boyunca geçerli indeks aralığını döndürür.

Ayrıca [`size`](@ref) ve [özel indekslere sahip diziler](@ref man-custom-indices) konulu kılavuz bölümüne bakın.

# Örnekler

```jldoctest
julia> A = fill(1, (5,6,7));

julia> axes(A, 2)
Base.OneTo(6)

julia> axes(A, 4) == 1:1  # ndims(A) > d olan tüm boyutlar 1 boyutuna sahiptir
true
```

# Kullanım notu

Her bir indeks `AbstractUnitRange{<:Integer}` olmalıdır, ancak aynı zamanda özel indeksler kullanan bir tür de olabilir. Örneğin, bir alt küme gerekiyorsa, `begin`/`end` veya [`firstindex`](@ref)/[`lastindex`](@ref) gibi genelleştirilmiş indeksleme yapıları kullanın:

```julia
ix = axes(v, 1)
ix[2:end]          # örneğin Vektör için çalışır, ancak genel olarak başarısız olabilir
ix[(begin+1):end]  # genelleştirilmiş indeksler için çalışır
```
