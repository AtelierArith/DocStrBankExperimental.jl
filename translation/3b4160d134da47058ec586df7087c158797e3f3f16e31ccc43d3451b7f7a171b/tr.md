```
Channel{T=Any}(size::Int=0)
```

`T` türünde `size` nesnesini tutabilen bir `Channel` oluşturur. Dolu bir kanalda [`put!`](@ref) çağrıları, bir nesne [`take!`](@ref) ile çıkarılana kadar bloklanır.

`Channel(0)` tamponu olmayan bir kanal oluşturur. `put!`, eşleşen bir `take!` çağrılana kadar bloklanır. Ve tersine.

Diğer yapıcılar:

  * `Channel()`: varsayılan yapıcı, `Channel{Any}(0)` ile eşdeğerdir
  * `Channel(Inf)`: `Channel{Any}(typemax(Int))` ile eşdeğerdir
  * `Channel(sz)`: `Channel{Any}(sz)` ile eşdeğerdir

!!! compat "Julia 1.3"
    Varsayılan yapıcı `Channel()` ve varsayılan `size=0`, Julia 1.3'te eklendi.

