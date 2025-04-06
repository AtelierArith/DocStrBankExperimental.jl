```
all(p, itr) -> Bool
```

프레디케이트 `p`가 `itr`의 모든 요소에 대해 `true`를 반환하는지 확인하고, `p`가 `false`를 반환하는 `itr`의 첫 번째 항목을 만나는 즉시 `false`를 반환합니다(단락 회로). `true`에 대해 단락 회로를 사용하려면 [`any`](@ref)를 사용하세요.

입력에 [`missing`](@ref) 값이 포함되어 있으면, 모든 비어 있지 않은 값이 `true`인 경우(또는 입력에 `false` 값이 포함되어 있지 않은 경우) `missing`을 반환하며, [삼값 논리](https://en.wikipedia.org/wiki/Three-valued_logic)를 따릅니다.

# 예제

```jldoctest
julia> all(i->(4<=i<=6), [4,5,6])
true

julia> all(i -> (println(i); i < 3), 1:10)
1
2
3
false

julia> all(i -> i > 0, [1, missing])
missing

julia> all(i -> i > 0, [-1, missing])
false

julia> all(i -> i > 0, [1, 2])
true
```
