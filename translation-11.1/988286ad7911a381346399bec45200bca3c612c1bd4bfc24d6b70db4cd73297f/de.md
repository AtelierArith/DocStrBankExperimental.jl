```
DateTime(periods::Period...) -> DateTime
```

Konstruiere einen `DateTime`-Typ aus `Period`-Typteilen. Die Argumente können in beliebiger Reihenfolge angegeben werden. Nicht bereitgestellte DateTime-Teile haben den Standardwert `Dates.default(period)`.
