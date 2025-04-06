```
using
```

`using Foo` lädt das Modul oder Paket `Foo` und macht seine [`export`](@ref)ierten Namen für die direkte Verwendung verfügbar. Namen können auch über die Punkt-Syntax verwendet werden (z. B. `Foo.foo`, um auf den Namen `foo` zuzugreifen), unabhängig davon, ob sie `export`iert sind oder nicht. Siehe den [Handbuchabschnitt über Module](@ref modules) für Details.

!!! note
    Wenn zwei oder mehr Pakete/Module einen Namen exportieren und dieser Name in jedem der Pakete nicht dasselbe bezeichnet, und die Pakete über `using` ohne eine explizite Liste von Namen geladen werden, ist es ein Fehler, diesen Namen ohne Qualifikation zu referenzieren. Es wird daher empfohlen, dass Code, der darauf abzielt, zukunftskompatibel mit zukünftigen Versionen seiner Abhängigkeiten und von Julia zu sein, z. B. Code in veröffentlichten Paketen, die Namen auflistet, die er aus jedem geladenen Paket verwendet, z. B. `using Foo: Foo, f` anstelle von `using Foo`.

