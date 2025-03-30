```
hasmethod(f, t::Type{<:Tuple}[, kwnames]; world=get_world_counter()) -> Bool
```

Verilen genel işlevin, `world` tarafından verilen üst sınırda bir dünya yaşı ile eşleşen verilen `Tuple` argüman türlerine sahip bir yöntemi olup olmadığını belirleyin.

Eğer bir anahtar argüman adı `kwnames` tuple'ı sağlanmışsa, bu aynı zamanda `f`'nin `t` ile eşleşen yönteminin verilen anahtar argüman adlarına sahip olup olmadığını da kontrol eder. Eğer eşleşen yöntem değişken sayıda anahtar argüman kabul ediyorsa, örneğin `kwargs...` ile, `kwnames` içinde verilen herhangi bir ad geçerli kabul edilir. Aksi takdirde, sağlanan adlar yöntemin anahtar argümanlarının bir alt kümesi olmalıdır.

Ayrıca bkz. [`applicable`](@ref).

!!! compat "Julia 1.2"
    Anahtar argüman adları sağlamak, Julia 1.2 veya daha yenisini gerektirir.


# Örnekler

```jldoctest
julia> hasmethod(length, Tuple{Array})
true

julia> f(; oranges=0) = oranges;

julia> hasmethod(f, Tuple{}, (:oranges,))
true

julia> hasmethod(f, Tuple{}, (:apples, :bananas))
false

julia> g(; xs...) = 4;

julia> hasmethod(g, Tuple{}, (:a, :b, :c, :d))  # g rastgele kwargs kabul eder
true
```
