```
with(f, (var::ScopedValue{T} => val)...)
```

`f`'yi `var`'ı `val` olarak ayarlayarak yeni bir dinamik kapsamda çalıştırın. `val`, `T` türüne dönüştürülecektir.

Ayrıca bakınız: [`ScopedValues.@with`](@ref), [`ScopedValues.ScopedValue`](@ref), [`ScopedValues.get`](@ref).

# Örnekler

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
