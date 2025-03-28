```
LibGit2.reftype(ref::GitReference) -> Cint
```

Devuelve un `Cint` correspondiente al tipo de `ref`:

  * `0` si la referencia es inválida
  * `1` si la referencia es un id de objeto
  * `2` si la referencia es simbólica
