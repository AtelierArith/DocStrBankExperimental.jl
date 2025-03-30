```
normpath(path::AbstractString) -> String
```

경로를 정규화하여 "." 및 ".." 항목을 제거하고 "/"를 시스템의 표준 경로 구분자로 변경합니다.

# 예제

```jldoctest
julia> normpath("/home/myuser/../example.jl")
"/home/example.jl"

julia> normpath("Documents/Julia") == joinpath("Documents", "Julia")
true
```
