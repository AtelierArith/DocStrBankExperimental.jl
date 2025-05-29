```
cubefittable(tab,o,fitsym;post=getpostfunction(o),kwargs...)
```

[`fittable`](@ref) を [`CubeTable`](@ref) `tab` に対して (Weighted-)OnlineStat `o` で実行し、`fitsym` で指定された値をループします。最後に、`TableAggregator` からの結果を出力データキューブに書き込みます。
