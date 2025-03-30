```
isabspath(path::AbstractString) -> Bool
```

경로가 절대 경로인지(루트 디렉토리에서 시작하는지) 확인합니다.

# 예제

```jldoctest
julia> isabspath("/home")
true

julia> isabspath("home")
false
```
