```
randperm!([rng=default_rng(),] A::Array{<:Integer})
```

Construye en `A` una permutación aleatoria de longitud `length(A)`. El argumento opcional `rng` especifica un generador de números aleatorios (ver [Números Aleatorios](@ref)). Para permutar aleatoriamente un vector arbitrario, consulta [`shuffle`](@ref) o [`shuffle!`](@ref).

# Ejemplos

```jldoctest
julia> randperm!(Xoshiro(123), Vector{Int}(undef, 4))
4-element Vector{Int64}:
 1
 4
 2
 3
```
