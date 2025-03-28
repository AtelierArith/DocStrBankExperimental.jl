```
with(f, (var::ScopedValue{T} => val)...)
```

Führen Sie `f` in einem neuen dynamischen Gültigkeitsbereich aus, wobei `var` auf `val` gesetzt ist. `val` wird in den Typ `T` konvertiert.

Siehe auch: [`ScopedValues.@with`](@ref), [`ScopedValues.ScopedValue`](@ref), [`ScopedValues.get`](@ref).

# Beispiele

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
