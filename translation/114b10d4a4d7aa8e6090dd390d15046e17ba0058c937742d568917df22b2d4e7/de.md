```
catch_exceptions(logger)
```

Gibt `true` zurück, wenn der Logger Ausnahmen erfassen soll, die während der Konstruktion von Protokolleinträgen auftreten. Standardmäßig werden Nachrichten erfasst.

Standardmäßig werden alle Ausnahmen erfasst, um zu verhindern, dass die Generierung von Protokollnachrichten das Programm zum Absturz bringt. Dies ermöglicht es den Benutzern, wenig genutzte Funktionen - wie z. B. Debug-Protokollierung - in einem Produktionssystem mit Zuversicht zu aktivieren.

Wenn Sie Protokollierung als Prüfpfad verwenden möchten, sollten Sie dies für Ihren Logger-Typ deaktivieren.
