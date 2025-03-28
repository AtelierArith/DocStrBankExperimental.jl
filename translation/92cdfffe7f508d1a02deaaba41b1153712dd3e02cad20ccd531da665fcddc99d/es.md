```
Base.hasfastin(T)
```

Determina si la computación `x ∈ collection` donde `collection::T` puede considerarse como una operación "rápida" (típicamente de complejidad constante o logarítmica). La definición `hasfastin(x) = hasfastin(typeof(x))` se proporciona por conveniencia para que se puedan pasar instancias en lugar de tipos. Sin embargo, la forma que acepta un argumento de tipo debe definirse para nuevos tipos.

El valor predeterminado para `hasfastin(T)` es `true` para subtipos de [`AbstractSet`](@ref), [`AbstractDict`](@ref) y [`AbstractRange`](@ref) y `false` en caso contrario.
