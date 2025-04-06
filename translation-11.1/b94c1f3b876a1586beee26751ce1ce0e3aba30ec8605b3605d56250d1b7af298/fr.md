```
RemoteException(captured)
```

Les exceptions lors des calculs distants sont capturées et relancées localement. Un `RemoteException` enveloppe le `pid` du travailleur et une exception capturée. Une `CapturedException` capture l'exception distante et une forme sérialisable de la pile d'appels lorsque l'exception a été levée.
