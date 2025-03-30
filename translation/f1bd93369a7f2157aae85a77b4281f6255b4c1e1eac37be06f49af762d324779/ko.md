```
istaskstarted(t::Task) -> Bool
```

작업이 실행되기 시작했는지 여부를 결정합니다.

# 예시

```jldoctest
julia> a3() = sum(i for i in 1:1000);

julia> b = Task(a3);

julia> istaskstarted(b)
false
```
