```
splitpath(path::AbstractString) -> Vector{String}
```

파일 경로를 모든 경로 구성 요소로 분할합니다. 이는 `joinpath`의 반대입니다. 경로에 있는 각 디렉토리 또는 파일에 대해 하나씩의 하위 문자열 배열을 반환하며, 루트 디렉토리가 있는 경우 포함됩니다.

!!! compat "Julia 1.1"
    이 함수는 최소한 Julia 1.1이 필요합니다.


# 예제

```jldoctest
julia> splitpath("/home/myuser/example.jl")
4-element Vector{String}:
 "/"
 "home"
 "myuser"
 "example.jl"
```
