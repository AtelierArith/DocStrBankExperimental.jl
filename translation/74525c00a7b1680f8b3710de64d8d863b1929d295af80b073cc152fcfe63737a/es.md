```
dlclose(::Nothing)
```

Para el patrón de uso muy común de

```
try
    hdl = dlopen(library_name)
    ... do something
finally
    dlclose(hdl)
end
```

Definimos un método `dlclose()` que acepta un parámetro de tipo `Nothing`, para que el código del usuario no tenga que cambiar su comportamiento en el caso de que `library_name` no se encontrara.
