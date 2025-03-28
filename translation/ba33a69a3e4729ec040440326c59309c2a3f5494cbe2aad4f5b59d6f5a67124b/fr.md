```
@inline
```

Donnez un indice au compilateur que cette fonction vaut la peine d'être intégrée.

Les petites fonctions n'ont généralement pas besoin de l'annotation `@inline`, car le compilateur le fait automatiquement. En utilisant `@inline` sur des fonctions plus grandes, un coup de pouce supplémentaire peut être donné au compilateur pour l'intégrer.

`@inline` peut être appliqué immédiatement avant une définition de fonction ou dans un corps de fonction.

```julia
# annoter une définition longue
@inline function longdef(x)
    ...
end

# annoter une définition courte
@inline shortdef(x) = ...

# annoter une fonction anonyme qu'un bloc `do` crée
f() do
    @inline
    ...
end
```

!!! compat "Julia 1.8"
    L'utilisation dans un corps de fonction nécessite au moins Julia 1.8.


---

```
@inline block
```

Donnez un indice au compilateur que les appels dans `block` valent la peine d'être intégrés.

```julia
# Le compilateur essaiera d'intégrer `f`
@inline f(...)

# Le compilateur essaiera d'intégrer `f`, `g` et `+`
@inline f(...) + g(...)
```

!!! note
    Une annotation de site d'appel a toujours la priorité sur l'annotation appliquée à la définition de la fonction appelée :

    ```julia
    @noinline function explicit_noinline(args...)
        # corps
    end

    let
        @inline explicit_noinline(args...) # sera intégré
    end
    ```


!!! note
    Lorsqu'il y a des annotations de site d'appel imbriquées, l'annotation la plus interne a la priorité :

    ```julia
    @noinline let a0, b0 = ...
        a = @inline f(a0)  # le compilateur essaiera d'intégrer cet appel
        b = f(b0)          # le compilateur ne tentera PAS d'intégrer cet appel
        return a, b
    end
    ```


!!! warning
    Bien qu'une annotation de site d'appel essaiera de forcer l'intégration indépendamment du modèle de coût, il y a encore des chances qu'elle ne réussisse pas. En particulier, les appels récursifs ne peuvent pas être intégrés même s'ils sont annotés comme `@inline`d.


!!! compat "Julia 1.8"
    L'annotation de site d'appel nécessite au moins Julia 1.8.

