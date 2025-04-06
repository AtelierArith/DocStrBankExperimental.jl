```
@with (var::ScopedValue{T} => val)... expr
```

Makroversion von `with`. Der Ausdruck `@with var=>val expr` bewertet `expr` in einem neuen dynamischen Gültigkeitsbereich mit `var`, das auf `val` gesetzt ist. `val` wird in den Typ `T` umgewandelt. `@with var=>val expr` ist äquivalent zu `with(var=>val) do expr end`, aber `@with` vermeidet die Erstellung einer Closure.

Siehe auch: [`ScopedValues.with`](@ref), [`ScopedValues.ScopedValue`](@ref), [`ScopedValues.get`](@ref).

# Beispiele

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
