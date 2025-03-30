```
isdir(path) -> Bool
```

`path`가 디렉토리인 경우 `true`를 반환하고, 그렇지 않으면 `false`를 반환합니다.

# 예제

```jldoctest
julia> isdir(homedir())
true

julia> isdir("not/a/directory")
false
```

또한 [`isfile`](@ref) 및 [`ispath`](@ref)를 참조하십시오.
