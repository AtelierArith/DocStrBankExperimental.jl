```
eachsplit(str::AbstractString, dlm; limit::Integer=0, keepempty::Bool=true)
eachsplit(str::AbstractString; limit::Integer=0, keepempty::Bool=false)
```

Divide `str` en las ocurrencias del delimitador(es) `dlm` y devuelve un iterador sobre las subcadenas. `dlm` puede ser cualquiera de los formatos permitidos por el primer argumento de [`findnext`](@ref) (es decir, como una cadena, expresión regular o una función), o como un solo carácter o colección de caracteres.

Si se omite `dlm`, por defecto se utiliza [`isspace`](@ref).

Los argumentos de palabra clave opcionales son:

  * `limit`: el tamaño máximo del resultado. `limit=0` implica sin máximo (por defecto)
  * `keepempty`: si los campos vacíos deben ser mantenidos en el resultado. El valor por defecto es `false` sin un argumento `dlm`, `true` con un argumento `dlm`.

Véase también [`split`](@ref).

!!! compat "Julia 1.8"
    La función `eachsplit` requiere al menos Julia 1.8.


# Ejemplos

```jldoctest
julia> a = "Ma.rch"
"Ma.rch"

julia> b = eachsplit(a, ".")
Base.SplitIterator{String, String}("Ma.rch", ".", 0, true)

julia> collect(b)
2-element Vector{SubString{String}}:
 "Ma"
 "rch"
```
