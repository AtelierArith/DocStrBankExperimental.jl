```
Some{T}
```

Ein Wrapper-Typ, der in `Union{Some{T}, Nothing}` verwendet wird, um zwischen der Abwesenheit eines Wertes ([`nothing`](@ref)) und der Anwesenheit eines `nothing`-Wertes (d.h. `Some(nothing)`) zu unterscheiden.

Verwenden Sie [`something`](@ref), um auf den Wert zuzugreifen, der von einem `Some`-Objekt umschlossen ist.
