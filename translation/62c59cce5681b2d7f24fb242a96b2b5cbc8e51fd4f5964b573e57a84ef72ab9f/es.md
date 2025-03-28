```
ispunct(c::AbstractChar) -> Bool
```

Prueba si un carácter pertenece a la categoría general de Unicode Puntuación, es decir, un carácter cuyo código de categoría comienza con 'P'.

# Ejemplos

```jldoctest
julia> ispunct('α')
false

julia> ispunct('/')
true

julia> ispunct(';')
true
```
