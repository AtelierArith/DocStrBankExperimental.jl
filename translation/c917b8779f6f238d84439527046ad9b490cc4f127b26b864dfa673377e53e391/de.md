```
issuccess(F::Faktorisierung)
```

Überprüfen, ob eine Faktorisierung einer Matrix erfolgreich war.

!!! kompatibel "Julia 1.6"
    `issuccess(::CholeskyPivoted)` erfordert Julia 1.6 oder höher.


# Beispiele

```jldoctest
julia> F = cholesky([1 0; 0 1]);

julia> issuccess(F)
true
```
