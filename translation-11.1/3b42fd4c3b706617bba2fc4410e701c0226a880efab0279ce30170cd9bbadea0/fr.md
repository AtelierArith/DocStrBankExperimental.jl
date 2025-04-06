```
Base.datatype_haspadding(dt::DataType) -> Bool
```

Renvoie si les champs des instances de ce type sont regroupés en mémoire, sans bits de remplissage intermédiaires (définis comme des bits dont la valeur n'impacte pas de manière unique le test d'égalité lorsqu'il est appliqué aux champs de la structure). Peut être appelé sur tout `isconcretetype`.
