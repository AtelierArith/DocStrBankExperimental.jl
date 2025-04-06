```
Broadcast.broadcastable(x)
```

Gibt entweder `x` oder ein Objekt wie `x` zurück, sodass es [`axes`](@ref), Indizierung unterstützt und sein Typ [`ndims`](@ref) unterstützt.

Wenn `x` Iteration unterstützt, sollte der zurückgegebene Wert die gleichen `axes` und Indizierungsverhalten wie [`collect(x)`](@ref) haben.

Wenn `x` kein `AbstractArray` ist, aber `axes`, Indizierung unterstützt und sein Typ `ndims` unterstützt, dann kann `broadcastable(::typeof(x))` implementiert werden, um einfach sich selbst zurückzugeben. Darüber hinaus, wenn `x` seinen eigenen [`BroadcastStyle`](@ref) definiert, muss es seine `broadcastable`-Methode definieren, um sich selbst zurückzugeben, damit der benutzerdefinierte Stil irgendeine Wirkung hat.

# Beispiele

```jldoctest
julia> Broadcast.broadcastable([1,2,3]) # wie `identity`, da Arrays bereits axes und Indizierung unterstützen
3-element Vector{Int64}:
 1
 2
 3

julia> Broadcast.broadcastable(Int) # Typen unterstützen keine axes, Indizierung oder Iteration, werden aber häufig als Skalare verwendet
Base.RefValue{Type{Int64}}(Int64)

julia> Broadcast.broadcastable("hello") # Strings brechen die Konvention der Übereinstimmung von Iteration und verhalten sich stattdessen wie ein Skalar
Base.RefValue{String}("hello")
```
