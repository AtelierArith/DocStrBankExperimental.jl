```
LAPACKException
```

Exception générique LAPACK lancée soit lors d'appels directs aux [fonctions LAPACK](@ref man-linalg-lapack-functions), soit lors d'appels à d'autres fonctions qui utilisent les fonctions LAPACK en interne mais qui manquent de gestion d'erreurs spécialisée. Le champ `info` contient des informations supplémentaires sur l'erreur sous-jacente et dépend de la fonction LAPACK qui a été invoquée.
