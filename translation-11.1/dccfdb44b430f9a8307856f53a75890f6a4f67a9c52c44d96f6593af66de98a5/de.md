```
ImmutableDict
```

`ImmutableDict` ist ein Wörterbuch, das als unveränderliche verkettete Liste implementiert ist, was optimal für kleine Wörterbücher ist, die über viele einzelne Einfügungen erstellt werden. Es ist zu beachten, dass es nicht möglich ist, einen Wert zu entfernen, obwohl er teilweise überschrieben und verborgen werden kann, indem ein neuer Wert mit demselben Schlüssel eingefügt wird.

```
ImmutableDict(KV::Pair)
```

Erstellen Sie einen neuen Eintrag im `ImmutableDict` für ein `key => value` Paar

  * verwenden Sie `(key => value) in dict`, um zu sehen, ob diese spezielle Kombination im Eigenschaften-Set enthalten ist
  * verwenden Sie `get(dict, key, default)`, um den aktuellsten Wert für einen bestimmten Schlüssel abzurufen
