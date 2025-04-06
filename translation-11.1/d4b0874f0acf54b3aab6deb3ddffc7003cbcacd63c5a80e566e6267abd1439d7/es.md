```
@__doc__(ex)
```

Macro de bajo nivel utilizado para marcar expresiones devueltas por un macro que deben ser documentadas. Si se marcan más de una expresión, entonces la misma cadena de documentación se aplica a cada expresión.

```
macro example(f)
    quote
        $(f)() = 0
        @__doc__ $(f)(x) = 1
        $(f)(x, y) = 2
    end |> esc
end
```

`@__doc__` no tiene efecto cuando un macro que lo utiliza no está documentado.
