```
enumerar(iter)
```

Un iterador que produce `(i, x)` donde `i` es un contador que comienza en 1, y `x` es el valor `i`-ésimo del iterador dado. Es útil cuando necesitas no solo los valores `x` sobre los que estás iterando, sino también el número de iteraciones hasta ahora.

Ten en cuenta que `i` puede no ser válido para indexar `iter`, o puede indexar un elemento diferente. Esto sucederá si `iter` tiene índices que no comienzan en 1, y puede suceder con cadenas, diccionarios, etc. Consulta el método `pares(IndexLinear(), iter)` si deseas asegurarte de que `i` sea un índice.

# Ejemplos

```jldoctest
julia> a = ["a", "b", "c"];

julia> for (index, value) in enumerate(a)
           println("$index $value")
       end
1 a
2 b
3 c

julia> str = "naïve";

julia> for (i, val) in enumerate(str)
           print("i = ", i, ", val = ", val, ", ")
           try @show(str[i]) catch e println(e) end
       end
i = 1, val = n, str[i] = 'n'
i = 2, val = a, str[i] = 'a'
i = 3, val = ï, str[i] = 'ï'
i = 4, val = v, StringIndexError("naïve", 4)
i = 5, val = e, str[i] = 'v'
```
