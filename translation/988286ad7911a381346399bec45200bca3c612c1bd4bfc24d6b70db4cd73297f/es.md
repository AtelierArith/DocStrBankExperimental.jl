```
DateTime(periods::Period...) -> DateTime
```

Construye un tipo `DateTime` a partir de partes del tipo `Period`. Los argumentos pueden estar en cualquier orden. Las partes de DateTime que no se proporcionen se establecerán en el valor de `Dates.default(period)`.
