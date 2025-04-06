```
dirname(path::AbstractString) -> String
```

경로의 디렉토리 부분을 가져옵니다. 경로의 끝에 있는 문자 ('/' 또는 '\')는 경로의 일부로 간주됩니다.

# 예제

```jldoctest
julia> dirname("/home/myuser")
"/home"

julia> dirname("/home/myuser/")
"/home/myuser"
```

또한 [`basename`](@ref)를 참조하세요.
