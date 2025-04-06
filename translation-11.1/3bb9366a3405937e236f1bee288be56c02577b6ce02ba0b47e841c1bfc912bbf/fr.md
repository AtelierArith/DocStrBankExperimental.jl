```
Time(period::TimePeriod...) -> Time
```

Construit un type `Time` à partir de parties de type `Period`. Les arguments peuvent être dans n'importe quel ordre. Les parties `Time` non fournies prendront par défaut la valeur de `Dates.default(period)`.
