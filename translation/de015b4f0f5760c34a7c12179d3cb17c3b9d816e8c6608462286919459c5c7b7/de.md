```
kill(p::Process, signum=Base.SIGTERM)
```

Sendet ein Signal an einen Prozess. Der Standardwert ist, den Prozess zu beenden. Gibt erfolgreich zurück, wenn der Prozess bereits beendet wurde, wirft jedoch einen Fehler, wenn das Beenden des Prozesses aus anderen Gründen fehlgeschlagen ist (z. B. unzureichende Berechtigungen).
