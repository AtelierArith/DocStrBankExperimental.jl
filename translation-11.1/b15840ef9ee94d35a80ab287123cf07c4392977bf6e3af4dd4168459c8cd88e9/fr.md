```
modf(x)
```

Renvoie un tuple `(fpart, ipart)` des parties fractionnaire et entière d'un nombre. Les deux parties ont le même signe que l'argument.

# Exemples

```jldoctest
julia> modf(3.5)
(0.5, 3.0)

julia> modf(-3.5)
(-0.5, -3.0)
```
