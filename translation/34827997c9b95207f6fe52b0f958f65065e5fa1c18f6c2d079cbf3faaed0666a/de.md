```
code_lowered(f, types; generated=true, debuginfo=:default)
```

Gibt ein Array der gesenkten Formen (IR) für die Methoden zurück, die der gegebenen generischen Funktion und dem Typsignatur entsprechen.

Wenn `generated` `false` ist, entsprechen die zurückgegebenen `CodeInfo`-Instanzen den Fallback-Implementierungen. Ein Fehler wird ausgelöst, wenn keine Fallback-Implementierung existiert. Wenn `generated` `true` ist, entsprechen diese `CodeInfo`-Instanzen den Methodenkörpern, die durch das Erweitern der Generatoren erzeugt werden.

Das Schlüsselwort `debuginfo` steuert die Menge an Code-Metadaten, die im Output vorhanden sind.

Beachten Sie, dass ein Fehler ausgelöst wird, wenn `types` keine Blatttypen sind, wenn `generated` `true` ist und eine der entsprechenden Methoden eine `@generated`-Methode ist.
