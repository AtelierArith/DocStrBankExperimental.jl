```
widen(x)
```

Wenn `x` ein Typ ist, gibt es einen "größeren" Typ zurück, der so definiert ist, dass arithmetische Operationen `+` und `-` garantiert nicht überlaufen oder an Präzision verlieren für jede Kombination von Werten, die der Typ `x` halten kann.

Für ganzzahlige Typen mit fester Größe, die weniger als 128 Bit haben, gibt `widen` einen Typ mit der doppelten Anzahl von Bits zurück.

Wenn `x` ein Wert ist, wird er in `widen(typeof(x))` umgewandelt.

# Beispiele

```jldoctest
julia> widen(Int32)
Int64

julia> widen(1.5f0)
1.5
```
