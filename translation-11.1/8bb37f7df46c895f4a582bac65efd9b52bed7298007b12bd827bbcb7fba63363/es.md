```
@with (var::ScopedValue{T} => val)... expr
```

Versión macro de `with`. La expresión `@with var=>val expr` evalúa `expr` en un nuevo ámbito dinámico con `var` establecido en `val`. `val` se convertirá al tipo `T`. `@with var=>val expr` es equivalente a `with(var=>val) do expr end`, pero `@with` evita crear un cierre.

Véase también: [`ScopedValues.with`](@ref), [`ScopedValues.ScopedValue`](@ref), [`ScopedValues.get`](@ref).

# Ejemplos

```jldoctest
julia> using Base.ScopedValues

julia> const a = ScopedValue(1);

julia> f(x) = a[] + x;

julia> @with a=>2 f(10)
12

julia> @with a=>3 begin
           x = 100
           f(x)
       end
103
```
