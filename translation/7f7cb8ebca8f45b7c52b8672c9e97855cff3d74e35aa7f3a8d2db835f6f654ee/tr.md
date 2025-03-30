```
@. expr
```

Herhangi bir işlev çağrısını veya operatörü `expr` içinde "nokta çağrısına" (örneğin `f(x)`'i `f.(x)`'e dönüştürmek) ve `expr` içindeki her atamayı "nokta atamasına" (örneğin `+=`'yi `.+=`'ye dönüştürmek) dönüştürün.

Eğer `expr` içinde seçilen işlev çağrıları için noktaları *kaçınmak* istiyorsanız, bu işlev çağrılarını `$` ile birleştirin. Örneğin, `@. sqrt(abs($sort(x)))` ifadesi `sqrt.(abs.(sort(x)))` ile eşdeğerdir (sort için nokta yok).

(`@.` ifadesi `@__dot__` çağrısına eşdeğerdir.)

# Örnekler

```jldoctest
julia> x = 1.0:3.0; y = similar(x);

julia> @. y = x + 3 * sin(x)
3-element Vector{Float64}:
 3.5244129544236893
 4.727892280477045
 3.4233600241796016
```
