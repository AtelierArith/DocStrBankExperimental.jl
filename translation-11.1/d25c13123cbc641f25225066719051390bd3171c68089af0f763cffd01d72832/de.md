```
@goto name
```

`@goto name` springt bedingungslos zu der Anweisung an der Stelle [`@label name`](@ref).

`@label` und `@goto` können keine Sprünge zu verschiedenen Top-Level-Anweisungen erstellen. Versuche führen zu einem Fehler. Um `@goto` dennoch zu verwenden, schließe `@label` und `@goto` in einen Block ein.
