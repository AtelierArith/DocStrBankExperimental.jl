```
count(
    pattern::Union{AbstractChar,AbstractString,AbstractPattern},
    string::AbstractString;
    overlap::Bool = false,
)
```

Devuelve el número de coincidencias para `pattern` en `string`. Esto es equivalente a llamar a `length(findall(pattern, string))` pero más eficiente.

Si `overlap=true`, las secuencias coincidentes pueden superponerse en los índices de la cadena original, de lo contrario, deben ser de rangos de caracteres disjuntos.

!!! compat "Julia 1.3"
    Este método requiere al menos Julia 1.3.


!!! compat "Julia 1.7"
    Usar un carácter como patrón requiere al menos Julia 1.7.


# Ejemplos

```jldoctest
julia> count('a', "JuliaLang")
2

julia> count(r"a(.)a", "cabacabac", overlap=true)
3

julia> count(r"a(.)a", "cabacabac")
2
```
