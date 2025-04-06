```
tempdir()
```

Obtient le chemin du répertoire temporaire. Sur Windows, `tempdir()` utilise la première variable d'environnement trouvée dans la liste ordonnée `TMP`, `TEMP`, `USERPROFILE`. Sur tous les autres systèmes d'exploitation, `tempdir()` utilise la première variable d'environnement trouvée dans la liste ordonnée `TMPDIR`, `TMP`, `TEMP` et `TEMPDIR`. Si aucune de ces variables n'est trouvée, le chemin `"/tmp"` est utilisé.
