```
LibGit2.reftype(ref::GitReference) -> Cint
```

Retourne un `Cint` correspondant au type de `ref` :

  * `0` si la référence est invalide
  * `1` si la référence est un identifiant d'objet
  * `2` si la référence est symbolique
