```
open(fd::OS_HANDLE) -> IO
```

Prenez un descripteur de fichier brut, enveloppez-le dans un type IO conscient de Julia et prenez possession de la poignée fd. Appelez `open(Libc.dup(fd))` pour éviter la capture de possession de la poignée originale.

!!! avertissement
    Ne l'appelez pas sur une poignée qui est déjà possédée par une autre partie du système.

