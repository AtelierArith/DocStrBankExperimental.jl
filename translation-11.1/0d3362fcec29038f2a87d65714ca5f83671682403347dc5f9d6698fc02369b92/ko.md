```
pwd() -> String
```

현재 작업 디렉토리를 가져옵니다.

참고: [`cd`](@ref), [`tempdir`](@ref).

# 예제

```julia-repl
julia> pwd()
"/home/JuliaUser"

julia> cd("/home/JuliaUser/Projects/julia")

julia> pwd()
"/home/JuliaUser/Projects/julia"
```
