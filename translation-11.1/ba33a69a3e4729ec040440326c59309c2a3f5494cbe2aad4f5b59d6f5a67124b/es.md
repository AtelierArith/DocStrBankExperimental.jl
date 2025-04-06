```
@inline
```

Dale una pista al compilador de que esta función merece ser inlined.

Las funciones pequeñas típicamente no necesitan la anotación `@inline`, ya que el compilador lo hace automáticamente. Al usar `@inline` en funciones más grandes, se puede dar un empujón adicional al compilador para que las inlined.

`@inline` se puede aplicar inmediatamente antes de una definición de función o dentro de un cuerpo de función.

```julia
# anotar definición de forma larga
@inline function longdef(x)
    ...
end

# anotar definición de forma corta
@inline shortdef(x) = ...

# anotar función anónima que crea un bloque `do`
f() do
    @inline
    ...
end
```

!!! compat "Julia 1.8"
    El uso dentro de un cuerpo de función requiere al menos Julia 1.8.


---

```
@inline block
```

Dale una pista al compilador de que las llamadas dentro de `block` merecen ser inlined.

```julia
# El compilador intentará inlined `f`
@inline f(...)

# El compilador intentará inlined `f`, `g` y `+`
@inline f(...) + g(...)
```

!!! note
    Una anotación de sitio de llamada siempre tiene precedencia sobre la anotación aplicada a la definición de la función llamada:

    ```julia
    @noinline function explicit_noinline(args...)
        # cuerpo
    end

    let
        @inline explicit_noinline(args...) # será inlined
    end
    ```


!!! note
    Cuando hay anotaciones de sitio de llamada anidadas, la anotación más interna tiene precedencia:

    ```julia
    @noinline let a0, b0 = ...
        a = @inline f(a0)  # el compilador intentará inlined esta llamada
        b = f(b0)          # el compilador NO intentará inlined esta llamada
        return a, b
    end
    ```


!!! warning
    Aunque una anotación de sitio de llamada intentará forzar el inlining independientemente del modelo de costos, aún hay posibilidades de que no pueda tener éxito. Especialmente, las llamadas recursivas no pueden ser inlined incluso si están anotadas como `@inline`d.


!!! compat "Julia 1.8"
    La anotación de sitio de llamada requiere al menos Julia 1.8.

