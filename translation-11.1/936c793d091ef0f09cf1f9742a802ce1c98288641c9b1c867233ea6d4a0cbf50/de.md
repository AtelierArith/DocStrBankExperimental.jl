```
getproperty(value, name::Symbol)
getproperty(value, name::Symbol, order::Symbol)
```

Die Syntax `a.b` ruft `getproperty(a, :b)` auf. Die Syntax `@atomic order a.b` ruft `getproperty(a, :b, :order)` auf und die Syntax `@atomic a.b` ruft `getproperty(a, :b, :sequentially_consistent)` auf.

# Beispiele

```jldoctest
julia> struct MyType{T <: Number}
           x::T
       end

julia> function Base.getproperty(obj::MyType, sym::Symbol)
           if sym === :special
               return obj.x + 1
           else # fallback to getfield
               return getfield(obj, sym)
           end
       end

julia> obj = MyType(1);

julia> obj.special
2

julia> obj.x
1
```

Man sollte `getproperty` nur dann überladen, wenn es notwendig ist, da es verwirrend sein kann, wenn das Verhalten der Syntax `obj.f` ungewöhnlich ist. Beachten Sie auch, dass die Verwendung von Methoden oft vorzuziehen ist. Siehe auch diese Stilrichtlinien-Dokumentation für weitere Informationen: [Bevorzugen Sie exportierte Methoden gegenüber direktem Feldzugriff](@ref).

Siehe auch [`getfield`](@ref Core.getfield), [`propertynames`](@ref Base.propertynames) und [`setproperty!`](@ref Base.setproperty!).
