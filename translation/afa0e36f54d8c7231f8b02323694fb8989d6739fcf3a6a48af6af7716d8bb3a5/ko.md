```
intersect(s, itrs...)
∩(s, itrs...)
```

모든 인수에 나타나는 요소를 포함하는 집합을 구성합니다.

첫 번째 인수는 반환되는 컨테이너의 종류를 제어합니다. 이것이 배열인 경우, 요소가 처음 나타나는 순서를 유지합니다.

유니코드 `∩`는 Julia REPL에서 `\cap`을 입력한 후 탭을 눌러 입력할 수 있으며, 많은 편집기에서도 가능합니다. 이는 중위 연산자로, `s ∩ itr`과 같이 사용할 수 있습니다.

또한 [`setdiff`](@ref), [`isdisjoint`](@ref), [`issubset`](@ref Base.issubset), [`issetequal`](@ref)도 참조하십시오.

!!! compat "Julia 1.8"
    Julia 1.8부터 intersect는 두 입력의 타입 승격된 eltype의 eltype을 가진 결과를 반환합니다.


# 예제

```jldoctest
julia> intersect([1, 2, 3], [3, 4, 5])
1-element Vector{Int64}:
 3

julia> intersect([1, 4, 4, 5, 6], [6, 4, 6, 7, 8])
2-element Vector{Int64}:
 4
 6

julia> intersect(1:16, 7:99)
7:16

julia> (0, 0.0) ∩ (-0.0, 0)
1-element Vector{Real}:
 0

julia> intersect(Set([1, 2]), BitSet([2, 3]), 1.0:10.0)
Set{Float64} with 1 element:
  2.0
```
