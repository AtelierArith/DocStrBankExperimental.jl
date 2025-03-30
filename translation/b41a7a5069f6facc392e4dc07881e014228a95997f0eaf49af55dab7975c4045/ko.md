```
union(s, itrs...)
∪(s, itrs...)
```

모든 인수에서 고유한 요소를 포함하는 객체를 생성합니다.

첫 번째 인수는 반환되는 컨테이너의 종류를 제어합니다. 이것이 배열인 경우, 요소가 처음 나타나는 순서를 유지합니다.

유니코드 `∪`는 Julia REPL에서 `\cup`를 입력한 후 탭을 눌러 입력할 수 있으며, 많은 편집기에서도 가능합니다. 이것은 중위 연산자로, `s ∪ itr` 형태로 사용할 수 있습니다.

또한 [`unique`](@ref), [`intersect`](@ref), [`isdisjoint`](@ref), [`vcat`](@ref), [`Iterators.flatten`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> union([1, 2], [3])
3-element Vector{Int64}:
 1
 2
 3

julia> union([4 2 3 4 4], 1:3, 3.0)
4-element Vector{Float64}:
 4.0
 2.0
 3.0
 1.0

julia> (0, 0.0) ∪ (-0.0, NaN)
3-element Vector{Real}:
   0
  -0.0
 NaN

julia> union(Set([1, 2]), 2:3)
Set{Int64} with 3 elements:
  2
  3
  1
```
