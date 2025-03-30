```
all(itr) -> Bool
```

부울 컬렉션의 모든 요소가 `true`인지 테스트하고, `itr`에서 첫 번째 `false` 값이 발견되는 즉시 `false`를 반환합니다(단락 회로). `true`에 대해 단락 회로를 사용하려면 [`any`](@ref)를 사용하십시오.

입력에 [`missing`](@ref) 값이 포함되어 있으면, 모든 비어 있지 않은 값이 `true`인 경우(또는 입력에 `false` 값이 포함되어 있지 않은 경우) `missing`을 반환하며, 이는 [삼값 논리](https://en.wikipedia.org/wiki/Three-valued_logic)를 따릅니다.

또한 참조: [`all!`](@ref), [`any`](@ref), [`count`](@ref), [`&`](@ref), , [`&&`](@ref), [`allunique`](@ref).

# 예제

```jldoctest
julia> a = [true,false,false,true]
4-element Vector{Bool}:
 1
 0
 0
 1

julia> all(a)
false

julia> all((println(i); v) for (i, v) in enumerate(a))
1
2
false

julia> all([missing, false])
false

julia> all([true, missing])
missing
```
