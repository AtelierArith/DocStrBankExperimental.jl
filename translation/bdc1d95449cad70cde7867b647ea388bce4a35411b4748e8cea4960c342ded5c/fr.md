```
open(command, mode::AbstractString, stdio=devnull)
```

Exécute `command` de manière asynchrone. Comme `open(command, stdio; read, write)` sauf qu'il spécifie les indicateurs de lecture et d'écriture via une chaîne de mode au lieu d'arguments de mot-clé. Les chaînes de mode possibles sont :

| Mode | Description       | Mots-clés                   |
|:---- |:----------------- |:--------------------------- |
| `r`  | lecture           | aucun                       |
| `w`  | écriture          | `write = true`              |
| `r+` | lecture, écriture | `read = true, write = true` |
| `w+` | lecture, écriture | `read = true, write = true` |
