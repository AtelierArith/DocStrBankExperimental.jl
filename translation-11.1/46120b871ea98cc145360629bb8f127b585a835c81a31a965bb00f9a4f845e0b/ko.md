```
evalfile(path::AbstractString, args::Vector{String}=String[])
```

파일을 익명 모듈에 로드하고 [`include`](@ref)를 사용하여 모든 표현식을 평가한 후 마지막 표현식의 값을 반환합니다. 선택적 `args` 인수는 스크립트의 입력 인수(즉, 전역 `ARGS` 변수)를 설정하는 데 사용할 수 있습니다. 정의(예: 메서드, 전역 변수)는 익명 모듈에서 평가되며 현재 모듈에 영향을 미치지 않습니다.

# 예제

```jldoctest
julia> write("testfile.jl", """
           @show ARGS
           1 + 1
       """);

julia> x = evalfile("testfile.jl", ["ARG1", "ARG2"]);
ARGS = ["ARG1", "ARG2"]

julia> x
2

julia> rm("testfile.jl")
```
