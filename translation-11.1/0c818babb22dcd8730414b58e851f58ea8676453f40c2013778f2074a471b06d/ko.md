```
promote_shape(s1, s2)
```

두 배열의 형태가 호환되는지 확인하고, 후행 단일 차원을 허용하며, 더 많은 차원을 가진 형태를 반환합니다.

# 예제

```jldoctest
julia> a = fill(1, (3,4,1,1,1));

julia> b = fill(1, (3,4));

julia> promote_shape(a,b)
(Base.OneTo(3), Base.OneTo(4), Base.OneTo(1), Base.OneTo(1), Base.OneTo(1))

julia> promote_shape((2,3,1,4), (2, 3, 1, 4, 1))
(2, 3, 1, 4, 1)
```
