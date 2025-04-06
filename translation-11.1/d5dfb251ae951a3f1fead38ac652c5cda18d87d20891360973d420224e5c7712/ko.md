```
@coalesce(x...)
```

단축 평가 버전의 [`coalesce`](@ref).

# 예제

```jldoctest
julia> f(x) = (println("f($x)"); missing);

julia> a = 1;

julia> a = @coalesce a f(2) f(3) error("`a`는 여전히 누락되었습니다")
1

julia> b = missing;

julia> b = @coalesce b f(2) f(3) error("`b`는 여전히 누락되었습니다")
f(2)
f(3)
ERROR: `b`는 여전히 누락되었습니다
[...]
```

!!! compat "Julia 1.7"
    이 매크로는 Julia 1.7부터 사용할 수 있습니다.

