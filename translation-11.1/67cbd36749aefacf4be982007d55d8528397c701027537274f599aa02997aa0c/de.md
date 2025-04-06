```
CompoundPeriod
```

Ein `CompoundPeriod` ist nützlich, um Zeiträume auszudrücken, die kein fester Vielfaches kleinerer Zeiträume sind. Zum Beispiel ist "ein Jahr und ein Tag" keine feste Anzahl von Tagen, kann aber mit einem `CompoundPeriod` ausgedrückt werden. Tatsächlich wird ein `CompoundPeriod` automatisch durch die Addition verschiedener Zeitraumtypen erzeugt, z.B. `Year(1) + Day(1)` ergibt ein `CompoundPeriod`-Ergebnis.
