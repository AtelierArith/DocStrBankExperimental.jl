```
deepcopy(x)
```

Erstellt eine tiefe Kopie von `x`: alles wird rekursiv kopiert, was zu einem vollständig unabhängigen Objekt führt. Zum Beispiel erzeugt das tiefe Kopieren eines Arrays tiefe Kopien aller Objekte, die es enthält, und produziert ein neues Array mit der konsistenten Beziehungsstruktur (z. B. wenn die ersten beiden Elemente dasselbe Objekt im ursprünglichen Array sind, werden die ersten beiden Elemente des neuen Arrays ebenfalls dasselbe `deepcopy`-Objekt sein). Das Aufrufen von `deepcopy` auf einem Objekt sollte im Allgemeinen denselben Effekt haben wie das Serialisieren und anschließende Deserialisieren.

Obwohl es normalerweise nicht notwendig ist, können benutzerdefinierte Typen das Standardverhalten von `deepcopy` überschreiben, indem sie eine spezialisierte Version der Funktion `deepcopy_internal(x::T, dict::IdDict)` definieren (die ansonsten nicht verwendet werden sollte), wobei `T` der Typ ist, für den spezialisiert werden soll, und `dict` die bisher innerhalb der Rekursion kopierten Objekte verfolgt. Innerhalb der Definition sollte `deepcopy_internal` anstelle von `deepcopy` verwendet werden, und die `dict`-Variable sollte entsprechend aktualisiert werden, bevor sie zurückgegeben wird.
