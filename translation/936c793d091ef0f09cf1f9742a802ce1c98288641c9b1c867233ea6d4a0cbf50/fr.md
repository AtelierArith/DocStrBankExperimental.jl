```
getproperty(value, name::Symbol)
getproperty(value, name::Symbol, order::Symbol)
```

La syntaxe `a.b` appelle `getproperty(a, :b)`. La syntaxe `@atomic order a.b` appelle `getproperty(a, :b, :order)` et la syntaxe `@atomic a.b` appelle `getproperty(a, :b, :sequentially_consistent)`.

# Exemples

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

On ne devrait surcharger `getproperty` que lorsque c'est nécessaire, car cela peut être déroutant si le comportement de la syntaxe `obj.f` est inhabituel. Notez également que l'utilisation de méthodes est souvent préférable. Voir aussi cette documentation de guide de style pour plus d'informations : [Préférer les méthodes exportées à l'accès direct aux champs](@ref).

Voir aussi [`getfield`](@ref Core.getfield), [`propertynames`](@ref Base.propertynames) et [`setproperty!`](@ref Base.setproperty!).
