```
mapfoldr(f, op, itr; [init])
```

Wie [`mapreduce`](@ref), aber mit garantierter rechter Assoziativität, wie in [`foldr`](@ref). Wenn angegeben, wird das Schlüsselwortargument `init` genau einmal verwendet. Im Allgemeinen ist es notwendig, `init` bereitzustellen, um mit leeren Sammlungen zu arbeiten.
