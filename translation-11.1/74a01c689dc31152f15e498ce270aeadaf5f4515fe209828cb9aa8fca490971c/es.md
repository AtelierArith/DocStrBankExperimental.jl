```
dt::Date + t::Time -> DateTime
```

La adición de un `Date` con un `Time` produce un `DateTime`. Las partes de hora, minuto, segundo y milisegundo del `Time` se utilizan junto con el año, mes y día del `Date` para crear el nuevo `DateTime`. Los microsegundos o nanosegundos no cero en el tipo `Time` resultarán en que se lance un `InexactError`.
