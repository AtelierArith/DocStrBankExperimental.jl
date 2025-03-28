```
mapfoldl(f, op, itr; [init])
```

Wie [`mapreduce`](@ref), aber mit garantierter linker Assoziativität, wie in [`foldl`](@ref). Wenn angegeben, wird das Schlüsselwort-Argument `init` genau einmal verwendet. Im Allgemeinen ist es notwendig, `init` bereitzustellen, um mit leeren Sammlungen zu arbeiten.
