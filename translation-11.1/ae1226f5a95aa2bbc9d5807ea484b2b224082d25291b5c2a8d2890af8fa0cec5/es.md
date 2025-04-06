`Text(s)`: Crea un objeto que renderiza `s` como texto plano.

```
Text("foo")
```

También puedes usar un flujo para grandes cantidades de datos:

```
Text() do io
  println(io, "foo")
end
```

!!! warning
    `Text` se exporta actualmente para mantener la compatibilidad hacia atrás, pero esta exportación está en desuso. Se recomienda usar este tipo como [`Docs.Text`](@ref) o importarlo explícitamente desde `Docs`.

