```
log(b,x)
```

Calcule le logarithme de `x` à la base `b`. Lance une [`DomainError`](@ref) pour les arguments [`Real`](@ref) négatifs.

# Exemples

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> log(4,8)
1.5

julia> log(4,2)
0.5

julia> log(-2, 3)
ERROR: DomainError with -2.0:
log a été appelé avec un argument réel négatif mais ne renverra qu'un résultat complexe s'il est appelé avec un argument complexe. Essayez log(Complex(x)).
Stacktrace:
 [1] throw_complex_domainerror(::Symbol, ::Float64) at ./math.jl:31
[...]

julia> log(2, -3)
ERROR: DomainError with -3.0:
log a été appelé avec un argument réel négatif mais ne renverra qu'un résultat complexe s'il est appelé avec un argument complexe. Essayez log(Complex(x)).
Stacktrace:
 [1] throw_complex_domainerror(::Symbol, ::Float64) at ./math.jl:31
[...]
```

!!! note
    Si `b` est une puissance de 2 ou 10, il convient d'utiliser [`log2`](@ref) ou [`log10`](@ref), car ceux-ci seront généralement plus rapides et plus précis. Par exemple,

    ```jldoctest
    julia> log(100,1000000)
    2.9999999999999996

    julia> log10(1000000)/2
    3.0
    ```

