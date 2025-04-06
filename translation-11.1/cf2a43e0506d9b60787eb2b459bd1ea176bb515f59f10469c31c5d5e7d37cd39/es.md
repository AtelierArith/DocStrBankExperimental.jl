```
DateTime
```

`DateTime` representa un punto en el tiempo según el calendario gregoriano proleptico. La resolución más fina del tiempo es milisegundo (es decir, microsegundos o nanosegundos no pueden ser representados por este tipo). El tipo soporta aritmética de punto fijo, y por lo tanto es propenso a desbordamientos (y subdesbordamientos). Una consecuencia notable es el redondeo al sumar un `Microsegundo` o un `Nanosegundo`:

```jldoctest
julia> dt = DateTime(2023, 8, 19, 17, 45, 32, 900)
2023-08-19T17:45:32.900

julia> dt + Millisecond(1)
2023-08-19T17:45:32.901

julia> dt + Microsecond(1000) # 1000us == 1ms
2023-08-19T17:45:32.901

julia> dt + Microsecond(999) # 999us redondeado a 1000us
2023-08-19T17:45:32.901

julia> dt + Microsecond(1499) # 1499 redondeado a 1000us
2023-08-19T17:45:32.901
```
