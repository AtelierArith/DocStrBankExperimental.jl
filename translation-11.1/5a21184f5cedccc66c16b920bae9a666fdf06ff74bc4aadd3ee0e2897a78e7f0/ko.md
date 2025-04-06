```
isfile(path) -> Bool
```

`path`가 일반 파일이면 `true`를 반환하고, 그렇지 않으면 `false`를 반환합니다.

# 예제

```jldoctest
julia> isfile(homedir())
false

julia> filename = "test_file.txt";

julia> write(filename, "Hello world!");

julia> isfile(filename)
true

julia> rm(filename);

julia> isfile(filename)
false
```

또한 [`isdir`](@ref) 및 [`ispath`](@ref)를 참조하십시오.
