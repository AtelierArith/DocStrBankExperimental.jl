```
remoteref_id(r::AbstractRemoteRef) -> RRID
```

`Future`s und `RemoteChannel`s werden durch Felder identifiziert:

  * `where` - bezieht sich auf den Knoten, an dem das zugrunde liegende Objekt/Speicher, auf das die Referenz verweist, tatsächlich existiert.
  * `whence` - bezieht sich auf den Knoten, von dem die Remote-Referenz erstellt wurde. Beachten Sie, dass dies sich von dem Knoten unterscheidet, an dem das zugrunde liegende Objekt, auf das verwiesen wird, tatsächlich existiert. Zum Beispiel würde der Aufruf von `RemoteChannel(2)` vom Master-Prozess zu einem `where`-Wert von 2 und einem `whence`-Wert von 1 führen.
  * `id` ist einzigartig für alle Referenzen, die von dem Worker erstellt wurden, der durch `whence` angegeben ist.

Zusammen identifizieren `whence` und `id` eindeutig eine Referenz über alle Worker hinweg.

`remoteref_id` ist eine Low-Level-API, die ein `RRID`-Objekt zurückgibt, das die `whence`- und `id`-Werte einer Remote-Referenz umschließt.
