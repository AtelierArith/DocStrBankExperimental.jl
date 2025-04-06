```
katalan
```

Die Konstante von Katalan.

# Beispiele

```jldoctest
julia> Base.MathConstants.catalan
katalan = 0.9159655941772...

julia> sum(log(x)/(1+x^2) for x in 1:0.01:10^6) * 0.01
0.9159466120554123
```
