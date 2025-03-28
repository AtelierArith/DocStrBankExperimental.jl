```
setfield!(value, name::Symbol, x, [order::Symbol])
setfield!(value, i::Int, x, [order::Symbol])
```

Asigna `x` a un campo nombrado en `value` de tipo compuesto. El `value` debe ser mutable y `x` debe ser un subtipo de `fieldtype(typeof(value), name)`. Además, se puede especificar un orden para esta operación. Si el campo fue declarado `@atomic`, esta especificación es obligatoria. De lo contrario, si no se declara como `@atomic`, debe ser `:not_atomic` si se especifica. Véase también [`setproperty!`](@ref Base.setproperty!).

# Ejemplos

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
