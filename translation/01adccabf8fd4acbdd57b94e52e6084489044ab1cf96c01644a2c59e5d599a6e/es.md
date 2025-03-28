```
split(str::AbstractString, dlm; limit::Integer=0, keepempty::Bool=true)
split(str::AbstractString; limit::Integer=0, keepempty::Bool=false)
```

Divide `str` en un arreglo de subcadenas en las ocurrencias del delimitador(es) `dlm`. `dlm` puede ser cualquiera de los formatos permitidos por el primer argumento de [`findnext`](@ref) (es decir, como una cadena, expresión regular o una función), o como un solo carácter o colección de caracteres.

Si se omite `dlm`, por defecto se utiliza [`isspace`](@ref).

Los argumentos opcionales son:

  * `limit`: el tamaño máximo del resultado. `limit=0` implica sin máximo (por defecto)
  * `keepempty`: si los campos vacíos deben ser mantenidos en el resultado. El valor por defecto es `false` sin un argumento `dlm`, `true` con un argumento `dlm`.

Ver también [`rsplit`](@ref), [`eachsplit`](@ref).

# Ejemplos

```jldoctest
julia> a = "Ma.rch"
"Ma.rch"

julia> split(a, ".")
2-element Vector{SubString{String}}:
 "Ma"
 "rch"
```
