```
log(b,x)
```

Berechnet den Logarithmus von `x` zur Basis `b`. Wirft [`DomainError`](@ref) für negative [`Real`](@ref) Argumente.

# Beispiele

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> log(4,8)
1.5

julia> log(4,2)
0.5

julia> log(-2, 3)
ERROR: DomainError mit -2.0:
log wurde mit einem negativen reellen Argument aufgerufen, gibt jedoch nur ein komplexes Ergebnis zurück, wenn es mit einem komplexen Argument aufgerufen wird. Versuchen Sie log(Complex(x)).
Stacktrace:
 [1] throw_complex_domainerror(::Symbol, ::Float64) at ./math.jl:31
[...]

julia> log(2, -3)
ERROR: DomainError mit -3.0:
log wurde mit einem negativen reellen Argument aufgerufen, gibt jedoch nur ein komplexes Ergebnis zurück, wenn es mit einem komplexen Argument aufgerufen wird. Versuchen Sie log(Complex(x)).
Stacktrace:
 [1] throw_complex_domainerror(::Symbol, ::Float64) at ./math.jl:31
[...]
```

!!! note
    Wenn `b` eine Potenz von 2 oder 10 ist, sollten [`log2`](@ref) oder [`log10`](@ref) verwendet werden, da diese typischerweise schneller und genauer sind. Zum Beispiel,

    ```jldoctest
    julia> log(100,1000000)
    2.9999999999999996

    julia> log10(1000000)/2
    3.0
    ```

