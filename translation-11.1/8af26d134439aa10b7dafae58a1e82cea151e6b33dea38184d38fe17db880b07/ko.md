```
UndefVarError(var::Symbol, [scope])
```

현재 범위에 기호가 정의되어 있지 않습니다.

# 예제

```jldoctest
julia> a
ERROR: UndefVarError: `a` not defined in `Main`

julia> a = 1;

julia> a
1
```
