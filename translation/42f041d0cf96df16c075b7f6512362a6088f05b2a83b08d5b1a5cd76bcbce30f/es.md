```
SpinLock()
```

Crea un bloqueo de giro no reentrante, de prueba-y-prueba-y-establecer. El uso recursivo resultará en un bloqueo. Este tipo de bloqueo solo debe usarse alrededor de código que toma poco tiempo para ejecutarse y no bloquea (por ejemplo, realizar E/S). En general, se debe usar [`ReentrantLock`](@ref) en su lugar.

Cada [`lock`](@ref) debe coincidir con un [`unlock`](@ref). Si [`!islocked(lck::SpinLock)`](@ref islocked) se cumple, [`trylock(lck)`](@ref trylock) tiene éxito a menos que haya otras tareas intentando mantener el bloqueo "al mismo tiempo".

Los bloqueos de giro de prueba-y-prueba-y-establecer son los más rápidos hasta aproximadamente 30 hilos en contención. Si tienes más contención que eso, se deben considerar diferentes enfoques de sincronización.
