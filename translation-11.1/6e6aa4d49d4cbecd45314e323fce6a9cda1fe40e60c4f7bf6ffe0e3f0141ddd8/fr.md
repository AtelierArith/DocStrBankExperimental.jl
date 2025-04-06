```
tryopen_exclusive(path::String, mode::Integer = 0o444) :: Union{Void, File}
```

Essayez de créer un nouveau fichier pour un accès exclusif en lecture-écriture, ne renvoyez rien s'il existe déjà.
