```
StepRange{T, S} <: OrdinalRange{T, S}
```

`T` türünde ve `S` türünde boşlukları olan elemanlarla aralıklar. Her bir eleman arasındaki adım sabittir ve aralık, `T` türünde bir `start` ve `stop` ile `S` türünde bir `step` cinsinden tanımlanır. Ne `T` ne de `S` kayan nokta türleri olmalıdır. `a:b:c` sözdizimi, `b != 0` ve `a`, `b` ve `c` tümü tam sayılar olduğunda bir `StepRange` oluşturur.

# Örnekler

```jldoctest
julia> collect(StepRange(1, Int8(2), 10))
5-element Vector{Int64}:
 1
 3
 5
 7
 9

julia> typeof(StepRange(1, Int8(2), 10))
StepRange{Int64, Int8}

julia> typeof(1:3:6)
StepRange{Int64, Int64}
```
