```
Base.datatype_alignment(dt::DataType) -> Int
```

Minimale Ausrichtung der Speicherzuweisung für Instanzen dieses Typs. Kann für jeden `isconcretetype` aufgerufen werden, obwohl es für Memory die Ausrichtung der Elemente und nicht des gesamten Objekts zurückgibt.
