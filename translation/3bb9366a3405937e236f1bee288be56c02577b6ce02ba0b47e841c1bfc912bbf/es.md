```
Time(period::TimePeriod...) -> Time
```

Construye un tipo `Time` a partir de partes del tipo `Period`. Los argumentos pueden estar en cualquier orden. Las partes de `Time` que no se proporcionen tendrán como valor por defecto el de `Dates.default(period)`.
