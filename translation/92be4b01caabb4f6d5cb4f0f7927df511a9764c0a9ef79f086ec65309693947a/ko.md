```
pop!(collection, key[, default])
```

`collection`에 `key`가 존재하면 해당 매핑을 삭제하고 반환하고, 그렇지 않으면 `default`를 반환하거나 `default`가 지정되지 않은 경우 오류를 발생시킵니다.

# 예제

```jldoctest
julia> d = Dict("a"=>1, "b"=>2, "c"=>3);

julia> pop!(d, "a")
1

julia> pop!(d, "d")
ERROR: KeyError: key "d" not found
Stacktrace:
[...]

julia> pop!(d, "e", 4)
4
```
