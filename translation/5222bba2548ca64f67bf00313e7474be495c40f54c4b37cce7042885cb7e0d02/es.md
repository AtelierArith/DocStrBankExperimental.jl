`HTML(s)`: Crea un objeto que renderiza `s` como html.

```
HTML("<div>foo</div>")
```

También puedes usar un flujo para grandes cantidades de datos:

```
HTML() do io
  println(io, "<div>foo</div>")
end
```

!!! warning
    `HTML` se exporta actualmente para mantener la compatibilidad hacia atrás, pero esta exportación está en desuso. Se recomienda usar este tipo como [`Docs.HTML`](@ref) o importarlo explícitamente desde `Docs`.

