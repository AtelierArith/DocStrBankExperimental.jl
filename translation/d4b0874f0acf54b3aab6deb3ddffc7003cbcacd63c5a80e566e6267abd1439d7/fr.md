```
@__doc__(ex)
```

Macro de bas niveau utilisée pour marquer les expressions retournées par une macro qui doivent être documentées. Si plus d'une expression est marquée, alors la même chaîne de documentation est appliquée à chaque expression.

```
macro example(f)
    quote
        $(f)() = 0
        @__doc__ $(f)(x) = 1
        $(f)(x, y) = 2
    end |> esc
end
```

`@__doc__` n'a aucun effet lorsqu'une macro qui l'utilise n'est pas documentée.
