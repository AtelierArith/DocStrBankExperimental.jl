```
Base.datatype_pointerfree(dt::DataType) -> Bool
```

Renvoie si les instances de ce type peuvent contenir des références à la mémoire gérée par le GC. Peut être appelé sur tout `isconcretetype`.
