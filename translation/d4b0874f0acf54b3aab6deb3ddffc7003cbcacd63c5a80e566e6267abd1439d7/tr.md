```
@__doc__(ex)
```

Düşük seviyeli makro, belgelenmesi gereken bir makro tarafından döndürülen ifadeleri işaretlemek için kullanılır. Birden fazla ifade işaretlenirse, aynı belge dizesi her bir ifadeye uygulanır.

```
macro example(f)
    quote
        $(f)() = 0
        @__doc__ $(f)(x) = 1
        $(f)(x, y) = 2
    end |> esc
end
```

`@__doc__`, kullanıldığı makro belgelenmediğinde hiçbir etkisi yoktur.
