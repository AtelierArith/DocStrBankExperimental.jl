```
floorceil(x::Period, precision::T) where T <: Union{TimePeriod, Week, Day} -> (T, T)
```

`Period`の`floor`と`ceil`を解像度`p`で同時に返します。個別に`floor`と`ceil`を呼び出すよりも効率的です。
