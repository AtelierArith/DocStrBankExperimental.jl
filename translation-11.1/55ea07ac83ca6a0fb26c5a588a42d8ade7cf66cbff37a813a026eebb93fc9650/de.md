```
print_test_results(ts::AbstractTestSet, depth_pad=0)
```

Druckt die Ergebnisse eines `AbstractTestSet` als formatierte Tabelle aus.

`depth_pad` bezieht sich darauf, wie viel Padding vor allen Ausgaben hinzugefügt werden soll.

Wird innerhalb von `Test.finish` aufgerufen, wenn das `finish`te Testset das oberste Testset ist.
