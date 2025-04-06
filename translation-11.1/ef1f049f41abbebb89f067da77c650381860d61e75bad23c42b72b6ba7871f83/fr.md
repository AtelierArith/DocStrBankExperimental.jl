```
@raw_str -> String
```

Créez une chaîne brute sans interpolation ni désévasion. L'exception est que les guillemets doivent toujours être échappés. Les barres obliques inverses échappent à la fois les guillemets et les autres barres obliques inverses, mais seulement lorsqu'une séquence de barres obliques inverses précède un caractère de citation. Ainsi, 2n barres obliques inverses suivies d'une citation codent n barres obliques inverses et la fin du littéral, tandis que 2n+1 barres obliques inverses suivies d'une citation codent n barres obliques inverses suivies d'un caractère de citation.

# Exemples

```jldoctest
julia> println(raw"\ $x")
\ $x

julia> println(raw"\"")
"

julia> println(raw"\\\"")
\"

julia> println(raw"\\x \\\"")
\\x \"
```
