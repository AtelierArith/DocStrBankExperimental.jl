```
SimpleLogger([stream,] min_level=Info)
```

Logger simpliste pour enregistrer tous les messages avec un niveau supérieur ou égal à `min_level` dans `stream`. Si le flux est fermé, les messages avec un niveau de journalisation supérieur ou égal à `Warn` seront enregistrés dans `stderr` et ceux en dessous dans `stdout`.
