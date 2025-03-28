```
@noinline
```

Dale una pista al compilador de que no debe inlining una función.

Las funciones pequeñas se inlinan automáticamente. Al usar `@noinline` en funciones pequeñas, se puede prevenir el auto-inlining.

`@noinline` se puede aplicar inmediatamente antes de una definición de función o dentro de un cuerpo de función.

```julia
# anotar definición de forma larga
@noinline function longdef(x)
    ...
end

# anotar definición de forma corta
@noinline shortdef(x) = ...

# anotar función anónima que crea un bloque `do`
f() do
    @noinline
    ...
end
```

!!! compat "Julia 1.8"
    El uso dentro de un cuerpo de función requiere al menos Julia 1.8.


---

```
@noinline block
```

Dale una pista al compilador de que no debe inlining las llamadas dentro de `block`.

```julia
# El compilador intentará no inlining `f`
@noinline f(...)

# El compilador intentará no inlining `f`, `g` y `+`
@noinline f(...) + g(...)
```

!!! note
    Una anotación de sitio de llamada siempre tiene precedencia sobre la anotación aplicada a la definición de la función llamada:

    ```julia
    @inline function explicit_inline(args...)
        # cuerpo
    end

    let
        @noinline explicit_inline(args...) # no será inlined
    end
    ```


!!! note
    Cuando hay anotaciones de sitio de llamada anidadas, la anotación más interna tiene precedencia:

    ```julia
    @inline let a0, b0 = ...
        a = @noinline f(a0)  # el compilador NO intentará inlining esta llamada
        b = f(b0)            # el compilador intentará inlining esta llamada
        return a, b
    end
    ```


!!! compat "Julia 1.8"
    La anotación de sitio de llamada requiere al menos Julia 1.8.


---

!!! note
    Si la función es trivial (por ejemplo, devuelve una constante) podría ser inlined de todos modos.

