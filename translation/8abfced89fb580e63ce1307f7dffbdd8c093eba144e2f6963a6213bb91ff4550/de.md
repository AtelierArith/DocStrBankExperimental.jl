```
serialize(stream::IO, value)
```

Schreibt einen beliebigen Wert in einen Stream in einem undurchsichtigen Format, sodass er von [`deserialize`](@ref) wieder gelesen werden kann. Der zurückgelesene Wert wird so identisch wie möglich zum Original sein, aber beachten Sie, dass `Ptr`-Werte als Null-Bitmuster (`NULL`) serialisiert werden.

Zuerst wird ein 8-Byte identifizierender Header in den Stream geschrieben. Um das Schreiben des Headers zu vermeiden, erstellen Sie einen `Serializer` und verwenden Sie ihn als erstes Argument für `serialize`. Siehe auch [`Serialization.writeheader`](@ref).

Das Datenformat kann sich in geringfügigen (1.x) Julia-Versionen ändern, aber Dateien, die von früheren 1.x-Versionen geschrieben wurden, bleiben lesbar. Die Hauptausnahme hiervon ist, wenn sich die Definition eines Typs in einem externen Paket ändert. In diesem Fall kann es notwendig sein, eine explizite kompatible Version des betroffenen Pakets in Ihrer Umgebung anzugeben. Das Umbenennen von Funktionen, selbst von privaten Funktionen, innerhalb von Paketen kann auch dazu führen, dass bestehende Dateien nicht mehr synchron sind. Anonyme Funktionen erfordern besondere Vorsicht: Da ihre Namen automatisch generiert werden, können geringfügige Codeänderungen dazu führen, dass sie umbenannt werden. Das Serialisieren von anonymen Funktionen sollte in Dateien, die für die langfristige Speicherung gedacht sind, vermieden werden.

In einigen Fällen muss die Wortgröße (32- oder 64-Bit) der lesenden und schreibenden Maschinen übereinstimmen. In selteneren Fällen muss auch das Betriebssystem oder die Architektur übereinstimmen, beispielsweise beim Einsatz von Paketen, die plattformabhängigen Code enthalten.
