```
with(f, (var::ScopedValue{T} => val)...)
```

Ejecuta `f` en un nuevo ámbito dinámico con `var` establecido en `val`. `val` se convertirá al tipo `T`.

Véase también: [`ScopedValues.@with`](@ref), [`ScopedValues.ScopedValue`](@ref), [`ScopedValues.get`](@ref).

# Ejemplos

```jldoctest
julia> using Base.ScopedValues

julia> a = ScopedValue(1);

julia> f(x) = a[] + x;

julia> f(10)
11

julia> with(a=>2) do
           f(10)
       end
12

julia> f(10)
11

julia> b = ScopedValue(2);

julia> g(x) = a[] + b[] + x;

julia> with(a=>10, b=>20) do
           g(30)
       end
60

julia> with(() -> a[] * b[], a=>3, b=>4)
12
```
