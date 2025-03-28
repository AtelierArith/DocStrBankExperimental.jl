```
@noinline
```

Donnez un indice au compilateur pour qu'il ne fasse pas d'inlining d'une fonction.

Les petites fonctions sont généralement inlinées automatiquement. En utilisant `@noinline` sur de petites fonctions, l'inlining automatique peut être empêché.

`@noinline` peut être appliqué immédiatement avant une définition de fonction ou dans le corps d'une fonction.

```julia
# annoter une définition longue
@noinline function longdef(x)
    ...
end

# annoter une définition courte
@noinline shortdef(x) = ...

# annoter une fonction anonyme créée par un bloc `do`
f() do
    @noinline
    ...
end
```

!!! compat "Julia 1.8"
    L'utilisation dans un corps de fonction nécessite au moins Julia 1.8.


---

```
@noinline block
```

Donnez un indice au compilateur pour qu'il ne fasse pas d'inlining des appels dans `block`.

```julia
# Le compilateur essaiera de ne pas inliner `f`
@noinline f(...)

# Le compilateur essaiera de ne pas inliner `f`, `g` et `+`
@noinline f(...) + g(...)
```

!!! note
    Une annotation de site d'appel a toujours la priorité sur l'annotation appliquée à la définition de la fonction appelée :

    ```julia
    @inline function explicit_inline(args...)
        # corps
    end

    let
        @noinline explicit_inline(args...) # ne sera pas inliné
    end
    ```


!!! note
    Lorsque des annotations de site d'appel sont imbriquées, l'annotation la plus interne a la priorité :

    ```julia
    @inline let a0, b0 = ...
        a = @noinline f(a0)  # le compilateur ne tentera PAS d'inliner cet appel
        b = f(b0)            # le compilateur tentera d'inliner cet appel
        return a, b
    end
    ```


!!! compat "Julia 1.8"
    L'annotation de site d'appel nécessite au moins Julia 1.8.


---

!!! note
    Si la fonction est triviale (par exemple, retournant une constante), elle pourrait quand même être inlinée.

