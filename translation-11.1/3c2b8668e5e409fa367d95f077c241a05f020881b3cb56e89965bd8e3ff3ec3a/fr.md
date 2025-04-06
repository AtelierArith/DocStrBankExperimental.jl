```
Base.datatype_alignment(dt::DataType) -> Int
```

Alignement minimum de l'allocation mémoire pour les instances de ce type. Peut être appelé sur tout `isconcretetype`, bien que pour Memory, il donnera l'alignement des éléments, et non de l'objet entier.
