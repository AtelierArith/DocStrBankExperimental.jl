```
Base.datatype_alignment(dt::DataType) -> Int
```

Alineación mínima de la asignación de memoria para instancias de este tipo. Se puede llamar en cualquier `isconcretetype`, aunque para Memory dará la alineación de los elementos, no del objeto completo.
