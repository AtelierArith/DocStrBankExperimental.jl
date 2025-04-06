```
Base.datatype_haspadding(dt::DataType) -> Bool
```

Devuelve si los campos de las instancias de este tipo están empaquetados en memoria, sin bits de relleno intermedios (definidos como bits cuyo valor no impacta de manera única en la prueba de igualdad cuando se aplica a los campos de la estructura). Se puede llamar a cualquier `isconcretetype`.
