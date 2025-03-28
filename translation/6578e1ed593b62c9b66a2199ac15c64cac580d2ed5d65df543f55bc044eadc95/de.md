```
artifact_exists(hash::SHA1; honor_overrides::Bool=true)
```

Gibt zurück, ob das angegebene Artefakt (identifiziert durch seinen sha1 git tree hash) auf der Festplatte existiert. Beachten Sie, dass es möglich ist, dass das angegebene Artefakt an mehreren Orten existiert (z. B. in mehreren Depots).

!!! compat "Julia 1.3"
    Diese Funktion erfordert mindestens Julia 1.3.

