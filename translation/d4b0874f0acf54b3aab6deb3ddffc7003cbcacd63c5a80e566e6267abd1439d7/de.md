```
@__doc__(ex)
```

Niedrigstufiges Makro, das verwendet wird, um Ausdrücke zu kennzeichnen, die von einem Makro zurückgegeben werden und dokumentiert werden sollten. Wenn mehr als ein Ausdruck markiert ist, wird derselbe Dokumentationsstring auf jeden Ausdruck angewendet.

```
macro example(f)
    quote
        $(f)() = 0
        @__doc__ $(f)(x) = 1
        $(f)(x, y) = 2
    end |> esc
end
```

`@__doc__` hat keine Wirkung, wenn ein Makro, das es verwendet, nicht dokumentiert ist.
