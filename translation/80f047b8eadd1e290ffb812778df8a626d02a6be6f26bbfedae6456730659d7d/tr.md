```
AssertionError([msg])
```

Doğrulanan koşul `true` olarak değerlendirilmedi. İsteğe bağlı argüman `msg`, açıklayıcı bir hata dizesidir.

# Örnekler

```jldoctest
julia> @assert false "this is not true"
HATA: AssertionError: this is not true
```

`AssertionError` genellikle [`@assert`](@ref) içinden fırlatılır.
