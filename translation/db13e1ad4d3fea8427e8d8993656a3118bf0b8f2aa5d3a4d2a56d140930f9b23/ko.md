```
cmp(a::AbstractString, b::AbstractString) -> Int
```

두 문자열을 비교합니다. 두 문자열의 길이가 같고 각 인덱스의 문자가 두 문자열에서 동일하면 `0`을 반환합니다. `a`가 `b`의 접두사이거나 `a`가 알파벳 순서에서 `b`보다 앞에 오면 `-1`을 반환합니다. `b`가 `a`의 접두사이거나 `b`가 알파벳 순서에서 `a`보다 앞에 오면 `1`을 반환합니다(기술적으로는 유니코드 코드 포인트에 의한 사전식 순서).

# 예제

```jldoctest
julia> cmp("abc", "abc")
0

julia> cmp("ab", "abc")
-1

julia> cmp("abc", "ab")
1

julia> cmp("ab", "ac")
-1

julia> cmp("ac", "ab")
1

julia> cmp("α", "a")
1

julia> cmp("b", "β")
-1
```
