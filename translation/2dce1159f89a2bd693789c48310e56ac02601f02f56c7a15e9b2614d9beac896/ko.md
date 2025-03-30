```
isdirpath(path::AbstractString) -> Bool
```

경로가 디렉토리를 참조하는지 여부를 결정합니다(예: 경로 구분자로 끝나는 경우).

# 예제

```jldoctest
julia> isdirpath("/home")
false

julia> isdirpath("/home/")
true
```
