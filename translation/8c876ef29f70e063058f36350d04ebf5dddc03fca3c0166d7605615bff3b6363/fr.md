```
GitShortHash(hash::GitHash, len::Integer)
```

Un identifiant d'objet git abrégé, qui peut être utilisé pour identifier un objet git lorsqu'il est unique, consistant des `len` premiers chiffres hexadécimaux de `hash` (les chiffres restants sont ignorés).
