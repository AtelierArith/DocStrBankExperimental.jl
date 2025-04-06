```
parse(type, str; base)
```

Analyse une chaîne de caractères comme un nombre. Pour les types `Integer`, une base peut être spécifiée (la valeur par défaut est 10). Pour les types à virgule flottante, la chaîne est analysée comme un nombre à virgule flottante décimal. Les types `Complex` sont analysés à partir de chaînes décimales de la forme `"R±Iim"` comme un `Complex(R,I)` du type demandé ; `"i"` ou `"j"` peuvent également être utilisés à la place de `"im"`, et `"R"` ou `"Iim"` sont également autorisés. Si la chaîne ne contient pas un nombre valide, une erreur est levée.

!!! compat "Julia 1.1"
    `parse(Bool, str)` nécessite au moins Julia 1.1.


# Exemples

```jldoctest
julia> parse(Int, "1234")
1234

julia> parse(Int, "1234", base = 5)
194

julia> parse(Int, "afc", base = 16)
2812

julia> parse(Float64, "1.2e-3")
0.0012

julia> parse(Complex{Float64}, "3.2e-1 + 4.5im")
0.32 + 4.5im
```
