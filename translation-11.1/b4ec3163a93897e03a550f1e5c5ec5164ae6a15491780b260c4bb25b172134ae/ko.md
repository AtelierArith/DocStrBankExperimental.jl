```
broadcast(f, As...)
```

함수 `f`를 배열, 튜플, 컬렉션, [`Ref`](@ref)s 및/또는 스칼라 `As`에 대해 브로드캐스트합니다.

브로드캐스팅은 컨테이너 인수의 요소와 `As`의 스칼라 자체에 대해 함수 `f`를 적용합니다. 단일 및 결측 차원은 값을 가상으로 반복하여 다른 인수의 범위에 맞게 확장됩니다. 기본적으로, `Number`s, `String`s, `Symbol`s, `Type`s, `Function`s 및 [`missing`](@ref) 및 [`nothing`](@ref)과 같은 일반적인 단일 항목을 포함하여 제한된 수의 유형만 스칼라로 간주됩니다. 다른 모든 인수는 요소별로 반복되거나 인덱싱됩니다.

결과 컨테이너 유형은 다음 규칙에 의해 결정됩니다:

  * 모든 인수가 스칼라 또는 0차원 배열인 경우, 언랩된 스칼라를 반환합니다.
  * 적어도 하나의 인수가 튜플이고 나머지가 스칼라 또는 0차원 배열인 경우, 튜플을 반환합니다.
  * 다른 모든 인수 조합은 기본적으로 `Array`를 반환하지만, 사용자 정의 컨테이너 유형은 인수로 나타날 때 결과를 사용자 정의하기 위해 자체 구현 및 승격과 유사한 규칙을 정의할 수 있습니다.

브로드캐스팅을 위한 특별한 구문이 존재합니다: `f.(args...)`는 `broadcast(f, args...)`와 동일하며, 중첩된 `f.(g.(args...))` 호출은 단일 브로드캐스트 루프로 융합됩니다.

# 예제

```jldoctest
julia> A = [1, 2, 3, 4, 5]
5-element Vector{Int64}:
 1
 2
 3
 4
 5

julia> B = [1 2; 3 4; 5 6; 7 8; 9 10]
5×2 Matrix{Int64}:
 1   2
 3   4
 5   6
 7   8
 9  10

julia> broadcast(+, A, B)
5×2 Matrix{Int64}:
  2   3
  5   6
  8   9
 11  12
 14  15

julia> parse.(Int, ["1", "2"])
2-element Vector{Int64}:
 1
 2

julia> abs.((1, -2))
(1, 2)

julia> broadcast(+, 1.0, (0, -2.0))
(1.0, -1.0)

julia> (+).([[0,2], [1,3]], Ref{Vector{Int}}([1,-1]))
2-element Vector{Vector{Int64}}:
 [1, 1]
 [2, 2]

julia> string.(("one","two","three","four"), ": ", 1:4)
4-element Vector{String}:
 "one: 1"
 "two: 2"
 "three: 3"
 "four: 4"

```
