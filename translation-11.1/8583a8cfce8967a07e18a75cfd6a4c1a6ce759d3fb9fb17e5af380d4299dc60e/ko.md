```
merge(a::NamedTuple, iterable)
```

키-값 쌍의 iterable을 명명된 튜플로 해석하고 병합을 수행합니다.

```jldoctest
julia> merge((a=1, b=2, c=3), [:b=>4, :d=>5])
(a = 1, b = 4, c = 3, d = 5)
```
