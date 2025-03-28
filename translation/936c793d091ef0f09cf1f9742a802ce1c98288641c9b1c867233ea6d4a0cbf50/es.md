```
getproperty(value, name::Symbol)
getproperty(value, name::Symbol, order::Symbol)
```

La sintaxis `a.b` llama a `getproperty(a, :b)`. La sintaxis `@atomic order a.b` llama a `getproperty(a, :b, :order)` y la sintaxis `@atomic a.b` llama a `getproperty(a, :b, :sequentially_consistent)`.

# Ejemplos

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

Uno debería sobrecargar `getproperty` solo cuando sea necesario, ya que puede ser confuso si el comportamiento de la sintaxis `obj.f` es inusual. También tenga en cuenta que usar métodos es a menudo preferible. Consulte también esta documentación de la guía de estilo para más información: [Prefer exported methods over direct field access](@ref).

Consulte también [`getfield`](@ref Core.getfield), [`propertynames`](@ref Base.propertynames) y [`setproperty!`](@ref Base.setproperty!).
