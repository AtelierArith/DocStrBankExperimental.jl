```
Channel{T=Any}(size::Int=0)
```

Konstruiert einen `Channel` mit einem internen Puffer, der maximal `size` Objekte vom Typ `T` halten kann. [`put!`](@ref) Aufrufe auf einem vollen Kanal blockieren, bis ein Objekt mit [`take!`](@ref) entfernt wird.

`Channel(0)` konstruiert einen unbuffered Kanal. `put!` blockiert, bis ein passendes `take!` aufgerufen wird. Und umgekehrt.

Weitere Konstruktoren:

  * `Channel()`: Standardkonstruktor, äquivalent zu `Channel{Any}(0)`
  * `Channel(Inf)`: äquivalent zu `Channel{Any}(typemax(Int))`
  * `Channel(sz)`: äquivalent zu `Channel{Any}(sz)`

!!! compat "Julia 1.3"
    Der Standardkonstruktor `Channel()` und die Standard `size=0` wurden in Julia 1.3 hinzugefügt.

