```
factorial(n::Integer)
```

Fakultät von `n`. Wenn `n` eine [`Integer`](@ref) ist, wird die Fakultät als Ganzzahl (mindestens 64 Bit) berechnet. Beachten Sie, dass dies überlaufen kann, wenn `n` nicht klein ist, aber Sie können `factorial(big(n))` verwenden, um das Ergebnis genau in beliebiger Präzision zu berechnen.

Siehe auch [`binomial`](@ref).

# Beispiele

```jldoctest
julia> factorial(6)
720

julia> factorial(21)
ERROR: OverflowError: 21 ist zu groß, um in der Tabelle nachgeschlagen zu werden; ziehen Sie in Betracht, stattdessen `factorial(big(21))` zu verwenden
Stacktrace:
[...]

julia> factorial(big(21))
51090942171709440000
```

# Externe Links

  * [Fakultät](https://en.wikipedia.org/wiki/Factorial) auf Wikipedia.
