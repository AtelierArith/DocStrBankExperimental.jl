```
invmod(n::Integer, T) where {T <: Base.BitInteger}
invmod(n::T) where {T <: Base.BitInteger}
```

Berechne das modulare Inverse von `n` im ganzzahligen Ring vom Typ `T`, d.h. modulo `2^N`, wobei `N = 8*sizeof(T)` (z.B. `N = 32` für `Int32`). Mit anderen Worten erfüllen diese Methoden die folgenden Identitäten:

```
n * invmod(n) == 1
(n * invmod(n, T)) % T == 1
(n % T) * invmod(n, T) == 1
```

Beachte, dass `*` hier die modulare Multiplikation im ganzzahligen Ring `T` ist.

Die Angabe des Modulus, der durch einen ganzzahligen Typ impliziert wird, als expliziter Wert ist oft unpraktisch, da der Modulus definitionsgemäß zu groß ist, um durch den Typ dargestellt zu werden.

Das modulare Inverse wird viel effizienter berechnet als der allgemeine Fall unter Verwendung des in https://arxiv.org/pdf/2204.04342.pdf beschriebenen Algorithmus.

!!! compat "Julia 1.11"
    Die Methoden `invmod(n)` und `invmod(n, T)` erfordern Julia 1.11 oder höher.


```
