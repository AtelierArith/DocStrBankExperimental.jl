```
retrieve(; kwargs...) -> data, lidict
```

"Exports" les résultats de profilage dans un format portable, retournant l'ensemble de toutes les traces de retour (`data`) et un dictionnaire qui associe les pointeurs d'instruction (spécifiques à la session) dans `data` à des valeurs `LineInfo` qui stockent le nom de fichier, le nom de fonction et le numéro de ligne. Cette fonction vous permet de sauvegarder les résultats de profilage pour une analyse future.
