```
listen(path::AbstractString) -> PipeServer
```

Créer et écouter sur un pipe nommé / socket de domaine UNIX.

!!! note
    La longueur du chemin sur Unix est limitée à quelque part entre 92 et 108 octets (cf. `man unix`).

