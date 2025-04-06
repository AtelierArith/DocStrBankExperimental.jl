```
Set{T} <: AbstractSet{T}
```

`Set`는 빠른 멤버십 테스트를 제공하는 가변 컨테이너입니다.

`Set`는 `in`, `union`, `intersect`와 같은 집합 연산의 효율적인 구현을 가지고 있습니다. `Set`의 요소는 `isequal`의 정의에 의해 결정된 고유한 요소입니다. `Set`의 요소 순서는 구현 세부 사항이며 신뢰할 수 없습니다.

참고: [`AbstractSet`](@ref), [`BitSet`](@ref), [`Dict`](@ref), [`push!`](@ref), [`empty!`](@ref), [`union!`](@ref), [`in`](@ref), [`isequal`](@ref)

# 예제

```jldoctest; filter = r"^  '.'"ma
julia> s = Set("aaBca")
Set{Char} with 3 elements:
  'a'
  'c'
  'B'

julia> push!(s, 'b')
Set{Char} with 4 elements:
  'a'
  'b'
  'B'
  'c'

julia> s = Set([NaN, 0.0, 1.0, 2.0]);

julia> -0.0 in s # isequal(0.0, -0.0) is false
false

julia> NaN in s # isequal(NaN, NaN) is true
true
```
