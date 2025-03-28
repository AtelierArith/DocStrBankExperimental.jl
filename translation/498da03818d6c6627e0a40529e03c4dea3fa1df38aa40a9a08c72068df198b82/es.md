```
daysinmonth(dt::TimeType) -> Int
```

Devuelve el número de días en el mes de `dt`. El valor será 28, 29, 30 o 31.

# Ejemplos

```jldoctest
julia> daysinmonth(Date("2000-01"))
31

julia> daysinmonth(Date("2001-02"))
28

julia> daysinmonth(Date("2000-02"))
29
```
