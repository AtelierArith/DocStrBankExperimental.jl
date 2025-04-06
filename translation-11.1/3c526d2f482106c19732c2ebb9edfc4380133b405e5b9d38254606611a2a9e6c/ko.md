```
get(collection, key, default)
```

주어진 키에 대해 저장된 값을 반환하며, 키에 대한 매핑이 없으면 주어진 기본값을 반환합니다.

!!! compat "Julia 1.7"
    튜플과 숫자의 경우, 이 함수는 최소한 Julia 1.7이 필요합니다.


# 예제

```jldoctest
julia> d = Dict("a"=>1, "b"=>2);

julia> get(d, "a", 3)
1

julia> get(d, "c", 3)
3
```
