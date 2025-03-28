```
RemoteException(captured)
```

Ausnahmen bei Remote-Berechnungen werden erfasst und lokal erneut ausgelöst. Eine `RemoteException` umschließt die `pid` des Arbeiters und eine erfasste Ausnahme. Eine `CapturedException` erfasst die Remote-Ausnahme und eine serialisierbare Form des Aufrufstapels, als die Ausnahme ausgelöst wurde.
