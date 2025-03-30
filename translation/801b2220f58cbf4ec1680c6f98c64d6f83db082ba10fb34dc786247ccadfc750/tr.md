```
rationalize([T<:Integer=Int,] x; tol::Real=eps(x))
```

Verilen tam sayı türünün bileşenleri ile `x` sayısını [`Rational`](@ref) sayısı olarak yaklaşık bir şekilde ifade edin. Sonuç, `x`'ten `tol` kadar bir farkla farklı olacaktır.

# Örnekler

```jldoctest
julia> rationalize(5.6)
28//5

julia> a = rationalize(BigInt, 10.3)
103//10

julia> typeof(numerator(a))
BigInt
```
