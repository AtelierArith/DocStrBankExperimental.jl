```
any(itr) -> Bool
```

부울 컬렉션의 요소 중 하나라도 `true`인지 테스트하고, `itr`에서 첫 번째 `true` 값을 찾는 즉시 `true`를 반환합니다(단락 회로). `false`에 대해 단락 회로를 사용하려면 [`all`](@ref)을 사용하십시오.

입력에 [`missing`](@ref) 값이 포함되어 있으면, 모든 비어 있지 않은 값이 `false`인 경우(또는 입력에 `true` 값이 포함되어 있지 않은 경우) `missing`을 반환하며, 이는 [삼값 논리](https://en.wikipedia.org/wiki/Three-valued_logic)를 따릅니다.

또한 참조: [`all`](@ref), [`count`](@ref), [`sum`](@ref), [`|`](@ref), , [`||`](@ref).

# 예제

```jldoctest
julia> a = [true,false,false,true]
4-element Vector{Bool}:
 1
 0
 0
 1

julia> any(a)
true

julia> any((println(i); v) for (i, v) in enumerate(a))
1
true

julia> any([missing, true])
true

julia> any([false, missing])
missing
```
