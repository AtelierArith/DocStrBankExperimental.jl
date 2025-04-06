```
Base.datatype_haspadding(dt::DataType) -> Bool
```

Gibt zurück, ob die Felder von Instanzen dieses Typs im Speicher gepackt sind, ohne dazwischenliegende Padding-Bits (definiert als Bits, deren Wert den Egal-Test, wenn er auf die Strukturfelder angewendet wird, nicht eindeutig beeinflusst). Kann auf jeden `isconcretetype` aufgerufen werden.
