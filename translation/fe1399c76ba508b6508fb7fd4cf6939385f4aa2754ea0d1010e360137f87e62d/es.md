```
DomainError(val)
DomainError(val, msg)
```

El argumento `val` a una función o constructor está fuera del dominio válido.

# Ejemplos

```jldoctest
julia> sqrt(-1)
ERROR: DomainError con -1.0:
sqrt fue llamado con un argumento real negativo pero solo devolverá un resultado complejo si se llama con un argumento complejo. Intenta sqrt(Complex(x)).
Stacktrace:
[...]
```
