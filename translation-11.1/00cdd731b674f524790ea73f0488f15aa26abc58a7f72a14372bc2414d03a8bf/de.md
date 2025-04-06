`BroadcastStyle` ist ein abstrakter Typ und eine Trait-Funktion, die verwendet wird, um das Verhalten von Objekten unter Broadcasting zu bestimmen. `BroadcastStyle(typeof(x))` gibt den Stil zurück, der mit `x` verbunden ist. Um das Broadcasting-Verhalten eines Typs anzupassen, kann man einen Stil deklarieren, indem man ein Typ-/Methoden-Paar definiert

```
struct MyContainerStyle <: BroadcastStyle end
Base.BroadcastStyle(::Type{<:MyContainer}) = MyContainerStyle()
```

Man schreibt dann Methode(n) (mindestens [`similar`](@ref)) die auf `Broadcasted{MyContainerStyle}` operieren. Es gibt auch mehrere vordefinierte Subtypen von `BroadcastStyle`, die Sie möglicherweise nutzen können; siehe das [Interfaces-Kapitel](@ref man-interfaces-broadcasting) für weitere Informationen.
