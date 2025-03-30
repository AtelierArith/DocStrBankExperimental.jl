```
istaskfailed(t::Task) -> Bool
```

작업이 예외가 발생하여 종료되었는지 여부를 결정합니다.

# 예제

```jldoctest
julia> a4() = error("작업 실패");

julia> b = Task(a4);

julia> istaskfailed(b)
false

julia> schedule(b);

julia> yield();

julia> istaskfailed(b)
true
```

!!! compat "Julia 1.3"
    이 함수는 최소한 Julia 1.3이 필요합니다.

