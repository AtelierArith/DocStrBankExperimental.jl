```
===(x,y) -> Bool
≡(x,y) -> Bool
```

Determina si `x` e `y` son idénticos, en el sentido de que ningún programa podría distinguirlos. Primero se comparan los tipos de `x` e `y`. Si son idénticos, los objetos mutables se comparan por dirección en memoria y los objetos inmutables (como los números) se comparan por contenido a nivel de bits. Esta función a veces se llama "egal". Siempre devuelve un valor `Bool`.

# Ejemplos

```jldoctest
julia> a = [1, 2]; b = [1, 2];

julia> a == b
true

julia> a === b
false

julia> a === a
true
```
