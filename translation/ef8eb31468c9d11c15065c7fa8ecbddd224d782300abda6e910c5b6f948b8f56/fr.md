```
parse_pidfile(file::Union{IO, String}) => (pid, hostname, age)
```

Tentez de parser notre format de fichier pid, remplaçant un élément par (0, "", 0.0), respectivement, pour toute lecture qui a échoué.
