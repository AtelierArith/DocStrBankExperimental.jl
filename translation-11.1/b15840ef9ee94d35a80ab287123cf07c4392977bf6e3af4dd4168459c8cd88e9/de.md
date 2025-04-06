```
modf(x)
```

Gibt ein Tupel `(fpart, ipart)` der Bruch- und Ganzzahlteile einer Zahl zurück. Beide Teile haben das gleiche Vorzeichen wie das Argument.

# Beispiele

```jldoctest
julia> modf(3.5)
(0.5, 3.0)

julia> modf(-3.5)
(-0.5, -3.0)
```
