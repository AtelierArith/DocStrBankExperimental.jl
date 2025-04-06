```
rand!([rng=default_rng()], A, [S=eltype(A)])
```

Diziyi `A`'yı rastgele değerlerle doldurur. Eğer `S` belirtilmişse (`S` bir tür veya bir koleksiyon olabilir, ayrıntılar için bkz. [`rand`](@ref)), değerler `S`'den rastgele seçilir. Bu, `copyto!(A, rand(rng, S, size(A)))` ile eşdeğerdir, ancak yeni bir dizi ayırmadan.

# Örnekler

```jldoctest
julia> rand!(Xoshiro(123), zeros(5))
5-element Vector{Float64}:
 0.521213795535383
 0.5868067574533484
 0.8908786980927811
 0.19090669902576285
 0.5256623915420473
```
