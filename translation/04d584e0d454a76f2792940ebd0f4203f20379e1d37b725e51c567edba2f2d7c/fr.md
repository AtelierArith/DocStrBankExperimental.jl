```
open(filename::AbstractString, [mode::AbstractString]; lock = true) -> IOStream
```

Syntaxe alternative pour open, où un spécificateur de mode basé sur une chaîne est utilisé au lieu des cinq booléens. Les valeurs de `mode` correspondent à celles de `fopen(3)` ou de Perl `open`, et sont équivalentes à la définition des groupes booléens suivants :

| Mode | Description                   | Mots-clés                      |
|:---- |:----------------------------- |:------------------------------ |
| `r`  | lire                          | aucun                          |
| `w`  | écrire, créer, tronquer       | `write = true`                 |
| `a`  | écrire, créer, ajouter        | `append = true`                |
| `r+` | lire, écrire                  | `read = true, write = true`    |
| `w+` | lire, écrire, créer, tronquer | `truncate = true, read = true` |
| `a+` | lire, écrire, créer, ajouter  | `append = true, read = true`   |

L'argument clé `lock` contrôle si les opérations seront verrouillées pour un accès multi-threadé sécurisé.

# Exemples

```jldoctest
julia> io = open("myfile.txt", "w");

julia> write(io, "Hello world!");

julia> close(io);

julia> io = open("myfile.txt", "r");

julia> read(io, String)
"Hello world!"

julia> write(io, "This file is read only")
ERROR: ArgumentError: write failed, IOStream is not writeable
[...]

julia> close(io)

julia> io = open("myfile.txt", "a");

julia> write(io, "This stream is not read only")
28

julia> close(io)

julia> rm("myfile.txt")
```

!!! compat "Julia 1.5"
    L'argument `lock` est disponible depuis Julia 1.5.

