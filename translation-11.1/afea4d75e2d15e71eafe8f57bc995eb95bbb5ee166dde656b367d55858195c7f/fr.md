```
redirect_stdout([stream]) -> stream
```

Créez un pipe vers lequel toute sortie [`stdout`](@ref) au niveau C et Julia sera redirigée. Retournez un flux représentant les extrémités du pipe. Les données écrites dans [`stdout`](@ref) peuvent maintenant être lues à partir de l'extrémité `rd` du pipe.

!!! note
    `stream` doit être un objet compatible, tel qu'un `IOStream`, `TTY`, [`Pipe`](@ref), socket ou `devnull`.


Voir aussi [`redirect_stdio`](@ref).
