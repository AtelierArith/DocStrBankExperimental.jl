```
rationalize([T<:Integer=Int,] x; tol::Real=eps(x))
```

Approxime le nombre à virgule flottante `x` en tant que nombre [`Rational`](@ref) avec des composants du type entier donné. Le résultat diffèrera de `x` de pas plus que `tol`.

# Exemples

```jldoctest
julia> rationalize(5.6)
28//5

julia> a = rationalize(BigInt, 10.3)
103//10

julia> typeof(numerator(a))
BigInt
```
