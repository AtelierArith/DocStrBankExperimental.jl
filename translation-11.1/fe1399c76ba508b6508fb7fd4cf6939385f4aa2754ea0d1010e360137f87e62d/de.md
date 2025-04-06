```
DomainError(val)
DomainError(val, msg)
```

Das Argument `val` für eine Funktion oder einen Konstruktor liegt außerhalb des gültigen Bereichs.

# Beispiele

```jldoctest
julia> sqrt(-1)
ERROR: DomainError mit -1.0:
sqrt wurde mit einem negativen reellen Argument aufgerufen, gibt jedoch nur ein komplexes Ergebnis zurück, wenn es mit einem komplexen Argument aufgerufen wird. Versuchen Sie sqrt(Complex(x)).
Stacktrace:
[...]
```
