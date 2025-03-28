```
dlsym_e(handle, sym)
```

Recherchez un symbole à partir d'un handle de bibliothèque partagée, renvoyez silencieusement `C_NULL` en cas d'échec de la recherche. Cette méthode est désormais obsolète au profit de `dlsym(handle, sym; throw_error=false)`.
