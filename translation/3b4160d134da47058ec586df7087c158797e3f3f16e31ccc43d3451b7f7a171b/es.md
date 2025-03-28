```
Channel{T=Any}(size::Int=0)
```

Construye un `Channel` con un búfer interno que puede contener un máximo de `size` objetos del tipo `T`. Las llamadas a [`put!`](@ref) en un canal lleno bloquean hasta que se elimine un objeto con [`take!`](@ref).

`Channel(0)` construye un canal sin búfer. `put!` bloquea hasta que se llama a un `take!` correspondiente. Y viceversa.

Otros constructores:

  * `Channel()`: constructor por defecto, equivalente a `Channel{Any}(0)`
  * `Channel(Inf)`: equivalente a `Channel{Any}(typemax(Int))`
  * `Channel(sz)`: equivalente a `Channel{Any}(sz)`

!!! compat "Julia 1.3"
    El constructor por defecto `Channel()` y el tamaño por defecto `size=0` se añadieron en Julia 1.3.

