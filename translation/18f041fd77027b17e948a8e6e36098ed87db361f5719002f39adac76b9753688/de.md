```
LibGit2.reftype(ref::GitReference) -> Cint
```

Gibt einen `Cint` zurück, der dem Typ von `ref` entspricht:

  * `0`, wenn die Referenz ungültig ist
  * `1`, wenn die Referenz eine Objekt-ID ist
  * `2`, wenn die Referenz symbolisch ist
