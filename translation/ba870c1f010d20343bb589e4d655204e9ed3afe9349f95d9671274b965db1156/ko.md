```
basename(path::AbstractString) -> String
```

경로의 파일 이름 부분을 가져옵니다.

!!! note
    이 함수는 Unix `basename` 프로그램과 약간 다릅니다. 여기서 후행 슬래시는 무시됩니다. 즉, `$ basename /foo/bar/`는 `bar`를 반환하지만, Julia의 `basename`은 빈 문자열 `""`을 반환합니다.


# 예제

```jldoctest
julia> basename("/home/myuser/example.jl")
"example.jl"

julia> basename("/home/myuser/")
""
```

또한 [`dirname`](@ref)를 참조하십시오.
