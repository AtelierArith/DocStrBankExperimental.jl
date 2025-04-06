```
istaskdone(t::Task) -> Bool
```

작업이 종료되었는지 확인합니다.

# 예제

```jldoctest
julia> a2() = sum(i for i in 1:1000);

julia> b = Task(a2);

julia> istaskdone(b)
false

julia> schedule(b);

julia> yield();

julia> istaskdone(b)
true
```
