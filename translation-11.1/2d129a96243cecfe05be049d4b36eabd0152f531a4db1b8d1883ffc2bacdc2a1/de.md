```
finish(ts::AbstractTestSet)
```

Führen Sie alle erforderlichen Abschlussverarbeitungen für das gegebene Testset durch. Dies wird von der `@testset`-Infrastruktur aufgerufen, nachdem ein Testblock ausgeführt wurde.

Benutzerdefinierte `AbstractTestSet`-Untertypen sollten `record` auf ihrem übergeordneten Element (sofern vorhanden) aufrufen, um sich dem Baum der Testergebnisse hinzuzufügen. Dies könnte wie folgt implementiert werden:

```julia
if get_testset_depth() != 0
    # Fügen Sie dieses Testset dem übergeordneten Testset hinzu
    parent_ts = get_testset()
    record(parent_ts, self)
    return self
end
```
