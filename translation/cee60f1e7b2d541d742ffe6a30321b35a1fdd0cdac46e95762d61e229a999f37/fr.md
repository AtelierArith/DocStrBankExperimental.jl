```
connect(path::AbstractString) -> PipeEndpoint
```

Se connecter au pipe nommé / socket de domaine UNIX à `path`.

!!! note
    La longueur du chemin sur Unix est limitée à quelque part entre 92 et 108 octets (cf. `man unix`).

