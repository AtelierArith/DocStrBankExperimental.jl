```
invmod(n::Integer, T) where {T <: Base.BitInteger}
invmod(n::T) where {T <: Base.BitInteger}
```

Calcula el inverso modular de `n` en el anillo entero de tipo `T`, es decir, módulo `2^N` donde `N = 8*sizeof(T)` (por ejemplo, `N = 32` para `Int32`). En otras palabras, estos métodos satisfacen las siguientes identidades:

```
n * invmod(n) == 1
(n * invmod(n, T)) % T == 1
(n % T) * invmod(n, T) == 1
```

Ten en cuenta que `*` aquí es multiplicación modular en el anillo entero, `T`.

Especificar el módulo implícito por un tipo de entero como un valor explícito es a menudo inconveniente, ya que el módulo es por definición demasiado grande para ser representado por el tipo.

El inverso modular se calcula de manera mucho más eficiente que el caso general utilizando el algoritmo descrito en https://arxiv.org/pdf/2204.04342.pdf.

!!! compat "Julia 1.11"
    Los métodos `invmod(n)` y `invmod(n, T)` requieren Julia 1.11 o posterior.

