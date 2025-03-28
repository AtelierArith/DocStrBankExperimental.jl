```
dt::Date + t::Time -> DateTime
```

Die Addition eines `Date` mit einem `Time` ergibt ein `DateTime`. Die Stunden-, Minuten-, Sekunden- und Millisekundenanteile des `Time` werden zusammen mit dem Jahr, Monat und Tag des `Date` verwendet, um das neue `DateTime` zu erstellen. Nicht-null Mikrosekunden oder Nanosekunden im `Time`-Typ führen zu einem `InexactError`.
