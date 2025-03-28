```
eachrsplit(str::AbstractString, dlm; limit::Integer=0, keepempty::Bool=true)
eachrsplit(str::AbstractString; limit::Integer=0, keepempty::Bool=false)
```

Devuelve un iterador sobre `SubString`s de `str`, producidos al dividirse en el(los) delimitador(es) `dlm`, y entregados en orden inverso (de derecha a izquierda). `dlm` puede ser cualquiera de los formatos permitidos por el primer argumento de [`findprev`](@ref) (es decir, una cadena, un solo carácter o una función), o una colección de caracteres.

Si se omite `dlm`, por defecto se utiliza [`isspace`](@ref), y `keepempty` por defecto es `false`.

Los argumentos de palabra clave opcionales son:

  * Si `limit > 0`, el iterador dividirá como máximo `limit - 1` veces antes de devolver el resto de la cadena sin dividir. `limit < 1` implica que no hay límite en las divisiones (por defecto).
  * `keepempty`: si los campos vacíos deben ser devueltos al iterar. El valor por defecto es `false` sin un argumento `dlm`, `true` con un argumento `dlm`.

Tenga en cuenta que a diferencia de [`split`](@ref), [`rsplit`](@ref) y [`eachsplit`](@ref), esta función itera los substrings de derecha a izquierda a medida que ocurren en la entrada.

Véase también [`eachsplit`](@ref), [`rsplit`](@ref).

!!! compat "Julia 1.11"
    Esta función requiere Julia 1.11 o posterior.


# Ejemplos

```jldoctest
julia> a = "Ma.r.ch";

julia> collect(eachrsplit(a, ".")) == ["ch", "r", "Ma"]
true

julia> collect(eachrsplit(a, "."; limit=2)) == ["ch", "Ma.r"]
true
```
