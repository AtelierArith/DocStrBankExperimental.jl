```
any(p, itr) -> Bool
```

조건부 `p`가 `itr`의 어떤 요소에 대해 `true`를 반환하는지 확인하고, `p`가 `true`를 반환하는 `itr`의 첫 번째 항목을 만나는 즉시 `true`를 반환합니다(단락 회로). `false`에 대해 단락 회로를 사용하려면 [`all`](@ref)을 사용하십시오.

입력에 [`missing`](@ref) 값이 포함되어 있으면, 모든 비어 있지 않은 값이 `false`인 경우(또는 입력에 `true` 값이 포함되어 있지 않은 경우) `missing`을 반환하며, [삼값 논리](https://en.wikipedia.org/wiki/Three-valued_logic)를 따릅니다.

# 예제

```jldoctest
julia> any(i->(4<=i<=6), [3,5,7])
true

julia> any(i -> (println(i); i > 3), 1:10)
1
2
3
4
true

julia> any(i -> i > 0, [1, missing])
true

julia> any(i -> i > 0, [-1, missing])
missing

julia> any(i -> i > 0, [-1, 0])
false
```
