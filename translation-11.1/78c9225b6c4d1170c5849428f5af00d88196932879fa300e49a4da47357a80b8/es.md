```
Base.datatype_pointerfree(dt::DataType) -> Bool
```

Devuelve si las instancias de este tipo pueden contener referencias a memoria gestionada por el recolector de basura. Se puede llamar en cualquier `isconcretetype`.
