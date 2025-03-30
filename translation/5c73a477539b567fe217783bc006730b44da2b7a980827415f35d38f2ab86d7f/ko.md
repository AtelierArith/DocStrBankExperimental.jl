```
oftype(x, y)
```

`y`를 `x`의 타입으로 변환합니다. 즉, `convert(typeof(x), y)`입니다.

# 예제

```jldoctest
julia> x = 4;

julia> y = 3.;

julia> oftype(x, y)
3

julia> oftype(y, x)
4.0
```
