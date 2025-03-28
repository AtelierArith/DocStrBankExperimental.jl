```
length(s::AbstractString) -> Int
length(s::AbstractString, i::Integer, j::Integer) -> Int
```

Devuelve el número de caracteres en la cadena `s` desde los índices `i` hasta `j`.

Esto se calcula como el número de índices de unidades de código desde `i` hasta `j` que son índices de caracteres válidos. Con solo un argumento de cadena, esto calcula el número de caracteres en toda la cadena. Con los argumentos `i` y `j`, calcula el número de índices entre `i` y `j` inclusive que son índices válidos en la cadena `s`. Además de los valores dentro de los límites, `i` puede tomar el valor fuera de los límites `ncodeunits(s) + 1` y `j` puede tomar el valor fuera de los límites `0`.

!!! note
    La complejidad temporal de esta operación es lineal en general. Es decir, tomará un tiempo proporcional al número de bytes o caracteres en la cadena porque cuenta el valor sobre la marcha. Esto contrasta con el método para arreglos, que es una operación de tiempo constante.


Véase también [`isvalid`](@ref), [`ncodeunits`](@ref), [`lastindex`](@ref), [`thisind`](@ref), [`nextind`](@ref), [`prevind`](@ref).

# Ejemplos

```jldoctest
julia> length("jμΛIα")
5
```
