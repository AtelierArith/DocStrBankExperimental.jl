```
Base.datatype_pointerfree(dt::DataType) -> Bool
```

Gibt zurück, ob Instanzen dieses Typs Verweise auf vom GC verwalteten Speicher enthalten können. Kann auf jedem `isconcretetype` aufgerufen werden.
