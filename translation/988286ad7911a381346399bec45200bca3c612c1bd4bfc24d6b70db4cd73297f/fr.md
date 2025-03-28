```
DateTime(periods::Period...) -> DateTime
```

Construit un type `DateTime` à partir de parties de type `Period`. Les arguments peuvent être dans n'importe quel ordre. Les parties de DateTime non fournies seront par défaut à la valeur de `Dates.default(period)`.
