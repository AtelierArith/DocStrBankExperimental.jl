```
RemoteException(captured)
```

Las excepciones en cálculos remotos se capturan y se vuelven a lanzar localmente. Un `RemoteException` envuelve el `pid` del trabajador y una excepción capturada. Una `CapturedException` captura la excepción remota y una forma serializable de la pila de llamadas cuando se produjo la excepción.
