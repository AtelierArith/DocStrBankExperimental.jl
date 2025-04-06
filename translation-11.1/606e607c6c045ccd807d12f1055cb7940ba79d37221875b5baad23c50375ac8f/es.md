```
ncodeunits(s::AbstractString) -> Int
```

Devuelve el número de unidades de código en una cadena. Los índices que están dentro de los límites para acceder a esta cadena deben satisfacer `1 ≤ i ≤ ncodeunits(s)`. No todos esos índices son válidos: pueden no ser el inicio de un carácter, pero devolverán un valor de unidad de código al llamar a `codeunit(s,i)`.

# Ejemplos

```jldoctest
julia> ncodeunits("The Julia Language")
18

julia> ncodeunits("∫eˣ")
6

julia> ncodeunits('∫'), ncodeunits('e'), ncodeunits('ˣ')
(3, 1, 2)
```

Ver también [`codeunit`](@ref), [`checkbounds`](@ref), [`sizeof`](@ref), [`length`](@ref), [`lastindex`](@ref).
