```
combine_axes(As...) -> Tuple
```

`As`의 모든 값에 대해 브로드캐스팅을 위한 결과 축을 결정합니다.

```jldoctest
julia> Broadcast.combine_axes([1], [1 2; 3 4; 5 6])
(Base.OneTo(3), Base.OneTo(2))

julia> Broadcast.combine_axes(1, 1, 1)
()
```
