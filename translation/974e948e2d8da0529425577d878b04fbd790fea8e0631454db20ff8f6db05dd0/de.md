```
gcd(x, y...)
```

Größter gemeinsamer (positiver) Teiler (oder null, wenn alle Argumente null sind). Die Argumente können ganze und rationale Zahlen sein.

!!! compat "Julia 1.4"
    Rationale Argumente erfordern Julia 1.4 oder höher.


# Beispiele

```jldoctest
julia> gcd(6, 9)
3

julia> gcd(6, -9)
3

julia> gcd(6, 0)
6

julia> gcd(0, 0)
0

julia> gcd(1//3, 2//3)
1//3

julia> gcd(1//3, -2//3)
1//3

julia> gcd(1//3, 2)
1//3

julia> gcd(0, 0, 10, 15)
5
```
