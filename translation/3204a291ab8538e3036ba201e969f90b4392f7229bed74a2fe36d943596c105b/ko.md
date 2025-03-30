```
@__DIR__ -> String
```

현재 디렉토리의 절대 경로를 문자열로 얻기 위한 매크로입니다.

스크립트에서 사용될 경우, `@__DIR__` 매크로 호출이 포함된 스크립트의 디렉토리를 반환합니다. REPL에서 실행되거나 `julia -e <expr>`로 평가될 경우, 현재 작업 디렉토리를 반환합니다.

# 예제

이 예제는 현재 작업 디렉토리와 다른 디렉토리에 간단한 스크립트를 생성하고 `@__DIR__`와 `pwd()`의 동작 차이를 보여줍니다:

```julia-repl
julia> cd("/home/JuliaUser") # 작업 디렉토리

julia> # /home/JuliaUser/Projects에 스크립트 생성
       open("/home/JuliaUser/Projects/test.jl","w") do io
           print(io, """
               println("@__DIR__ = ", @__DIR__)
               println("pwd() = ", pwd())
           """)
       end

julia> # 스크립트 디렉토리와 현재 작업 디렉토리 출력
       include("/home/JuliaUser/Projects/test.jl")
@__DIR__ = /home/JuliaUser/Projects
pwd() = /home/JuliaUser
```
