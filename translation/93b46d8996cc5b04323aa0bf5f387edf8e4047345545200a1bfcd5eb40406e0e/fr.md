```
setfield!(value, name::Symbol, x, [order::Symbol])
setfield!(value, i::Int, x, [order::Symbol])
```

Assignez `x` à un champ nommé dans `value` de type composite. Le `value` doit être mutable et `x` doit être un sous-type de `fieldtype(typeof(value), name)`. De plus, un ordre peut être spécifié pour cette opération. Si le champ a été déclaré `@atomic`, cette spécification est obligatoire. Sinon, s'il n'est pas déclaré comme `@atomic`, il doit être `:not_atomic` s'il est spécifié. Voir aussi [`setproperty!`](@ref Base.setproperty!).

# Exemples

```jldoctest
julia> mutable struct MyMutableStruct
           field::Int
       end

julia> a = MyMutableStruct(1);

julia> setfield!(a, :field, 2);

julia> getfield(a, :field)
2

julia> a = 1//2
1//2

julia> setfield!(a, :num, 3);
ERROR: setfield!: immutable struct of type Rational cannot be changed
```
