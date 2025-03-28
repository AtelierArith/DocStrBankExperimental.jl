```
names(x::Module; all::Bool = false, imported::Bool = false)
```

Erhalte einen Vektor der öffentlichen Namen eines `Module`, wobei veraltete Namen ausgeschlossen sind. Wenn `all` wahr ist, enthält die Liste auch nicht-öffentliche Namen, die im Modul definiert sind, veraltete Namen und vom Compiler generierte Namen. Wenn `imported` wahr ist, werden auch explizit aus anderen Modulen importierte Namen einbezogen. Die Namen werden in sortierter Reihenfolge zurückgegeben.

Als Sonderfall werden alle Namen, die in `Main` definiert sind, als "öffentlich" betrachtet, da es nicht idiomatisch ist, Namen aus `Main` ausdrücklich als öffentlich zu kennzeichnen.

!!! Hinweis     `sym ∈ names(SomeModule)` impliziert *nicht*, dass `isdefined(SomeModule, sym)`. `names` gibt Symbole zurück, die mit `public` oder `export` gekennzeichnet sind, auch wenn sie nicht im Modul definiert sind.

Siehe auch: [`Base.isexported`](@ref), [`Base.ispublic`](@ref), [`Base.@locals`](@ref), [`@__MODULE__`](@ref).
