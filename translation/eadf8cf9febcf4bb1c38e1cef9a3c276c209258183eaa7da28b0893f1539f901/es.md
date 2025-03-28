```
Broadcast.broadcastable(x)
```

Devuelve `x` o un objeto como `x` de tal manera que soporte [`axes`](@ref), indexación, y su tipo soporte [`ndims`](@ref).

Si `x` soporta iteración, el valor devuelto debe tener los mismos comportamientos de `axes` e indexación que [`collect(x)`](@ref).

Si `x` no es un `AbstractArray` pero soporta `axes`, indexación, y su tipo soporta `ndims`, entonces `broadcastable(::typeof(x))` puede ser implementado para simplemente devolverse a sí mismo. Además, si `x` define su propio [`BroadcastStyle`](@ref), entonces debe definir su método `broadcastable` para devolverse a sí mismo para que el estilo personalizado tenga algún efecto.

# Ejemplos

```jldoctest
julia> Broadcast.broadcastable([1,2,3]) # como `identity` ya que los arreglos ya soportan ejes e indexación
3-element Vector{Int64}:
 1
 2
 3

julia> Broadcast.broadcastable(Int) # Los tipos no soportan ejes, indexación, o iteración pero se utilizan comúnmente como escalares
Base.RefValue{Type{Int64}}(Int64)

julia> Broadcast.broadcastable("hello") # Las cadenas rompen la convención de coincidencia de iteración y actúan como un escalar en su lugar
Base.RefValue{String}("hello")
```
