```
Date(period::Period...) -> Date
```

Construye un tipo `Date` a partir de partes del tipo `Period`. Los argumentos pueden estar en cualquier orden. Las partes de `Date` que no se proporcionen se establecerán en el valor de `Dates.default(period)`.
