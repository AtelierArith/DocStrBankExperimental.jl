`BroadcastStyle` es un tipo abstracto y una función rasgo utilizada para determinar el comportamiento de los objetos bajo la difusión. `BroadcastStyle(typeof(x))` devuelve el estilo asociado con `x`. Para personalizar el comportamiento de difusión de un tipo, se puede declarar un estilo definiendo un par de tipo/método

```
struct MyContainerStyle <: BroadcastStyle end
Base.BroadcastStyle(::Type{<:MyContainer}) = MyContainerStyle()
```

Uno luego escribe método(s) (al menos [`similar`](@ref)) que operan en `Broadcasted{MyContainerStyle}`. También hay varios subtipos predefinidos de `BroadcastStyle` que puede que puedas aprovechar; consulta el [capítulo de Interfaces](@ref man-interfaces-broadcasting) para más información.
