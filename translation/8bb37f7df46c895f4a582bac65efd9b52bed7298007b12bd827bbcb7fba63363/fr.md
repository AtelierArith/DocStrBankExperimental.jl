```
@with (var::ScopedValue{T} => val)... expr
```

Version macro de `with`. L'expression `@with var=>val expr` évalue `expr` dans un nouveau scope dynamique avec `var` défini à `val`. `val` sera converti en type `T`. `@with var=>val expr` est équivalent à `with(var=>val) do expr end`, mais `@with` évite de créer une fermeture.

Voir aussi : [`ScopedValues.with`](@ref), [`ScopedValues.ScopedValue`](@ref), [`ScopedValues.get`](@ref).

# Exemples

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
