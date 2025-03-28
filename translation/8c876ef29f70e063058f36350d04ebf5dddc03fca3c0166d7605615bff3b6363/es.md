```
GitShortHash(hash::GitHash, len::Integer)
```

Un identificador de objeto git abreviado, que se puede utilizar para identificar un objeto git cuando es único, que consiste en los primeros `len` dígitos hexadecimales de `hash` (los dígitos restantes se ignoran).
