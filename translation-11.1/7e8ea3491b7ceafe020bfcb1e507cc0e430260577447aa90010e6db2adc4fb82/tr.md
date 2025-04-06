```
quote
```

`quote` bir blok içinde açıkça [`Expr`](@ref) yapıcıyı kullanmadan birden fazla ifade nesnesi oluşturur. Örneğin:

```julia
ex = quote
    x = 1
    y = 2
    x + y
end
```

Diğer alıntı yöntemlerinden farklı olarak, `:( ... )`, bu form ifade ağacına `QuoteNode` öğeleri ekler; bu, ağacı doğrudan manipüle ederken dikkate alınmalıdır. Diğer amaçlar için, `:( ... )` ve `quote .. end` blokları aynı şekilde işlenir.
