```
sort!(v; alg::Algorithm=defalg(v), lt=isless, by=identity, rev::Bool=false, order::Ordering=Forward)
```

벡터 `v`를 제자리에서 정렬합니다. 기본적으로 안정적인 알고리즘이 사용되며, 동등하게 비교되는 요소의 순서가 유지됩니다. 특정 알고리즘은 `alg` 키워드를 통해 선택할 수 있습니다(사용 가능한 알고리즘에 대한 내용은 [Sorting Algorithms](@ref)를 참조하십시오).

요소는 먼저 `by` 함수로 변환된 후, `lt` 함수 또는 `order`에 따라 비교됩니다. 마지막으로, `rev=true`인 경우 결과 순서가 반전됩니다(이는 전방 안정성을 유지합니다: 동등하게 비교되는 요소는 반전되지 않습니다). 현재 구현은 각 비교 전에 `by` 변환을 적용하며, 요소당 한 번만 적용되지 않습니다.

`isless`가 아닌 `lt`와 [`Base.Order.Forward`](@ref) 또는 [`Base.Order.Reverse`](@ref)가 아닌 `order`를 함께 사용하는 것은 허용되지 않습니다. 그렇지 않으면 모든 옵션은 독립적이며 가능한 모든 조합으로 함께 사용할 수 있습니다. `order`는 "by" 변환을 포함할 수 있으며, 이 경우 `by` 키워드로 정의된 후에 적용됩니다. `order` 값에 대한 자세한 내용은 [Alternate Orderings](@ref) 문서를 참조하십시오.

두 요소 간의 관계는 다음과 같이 정의됩니다(여기서 `rev=true`일 때 "less"와 "greater"가 교환됩니다):

  * `x`는 `y`보다 작으면 `lt(by(x), by(y))` (또는 `Base.Order.lt(order, by(x), by(y))`)가 true를 반환합니다.
  * `x`는 `y`보다 크면 `y`가 `x`보다 작습니다.
  * `x`와 `y`는 서로 작지 않으면 동등합니다("비교 불가능"은 때때로 "동등"의 동의어로 사용됩니다).

`sort!`의 결과는 모든 요소가 이전 요소보다 크거나 동등하다는 의미에서 정렬됩니다.

`lt` 함수는 엄격한 약한 순서를 정의해야 하며, 즉 다음과 같아야 합니다.

  * 비반사적: `lt(x, x)`는 항상 `false`를 반환해야 합니다.
  * 비대칭: `lt(x, y)`가 true를 반환하면 `lt(y, x)`는 false를 반환해야 합니다.
  * 추이적: `lt(x, y) && lt(y, z)`는 `lt(x, z)`를 의미합니다.
  * 동등성에서의 추이적: `!lt(x, y) && !lt(y, x)`와 `!lt(y, z) && !lt(z, y)`가 함께 `!lt(x, z) && !lt(z, x)`를 의미합니다. 즉, `x`와 `y`가 동등하고 `y`와 `z`가 동등하면 `x`와 `z`도 동등해야 합니다.

예를 들어 `<`는 `Int` 값에 대한 유효한 `lt` 함수이지만 `≤`는 그렇지 않습니다: 비반사성을 위반합니다. `Float64` 값의 경우 `<`조차도 유효하지 않습니다. 이는 네 번째 조건을 위반하기 때문입니다: `1.0`과 `NaN`은 동등하고 `NaN`과 `2.0`도 동등하지만 `1.0`과 `2.0`은 동등하지 않습니다.

또한 [`sort`](@ref), [`sortperm`](@ref), [`sortslices`](@ref), [`partialsort!`](@ref), [`partialsortperm`](@ref), [`issorted`](@ref), [`searchsorted`](@ref), [`insorted`](@ref), [`Base.Order.ord`](@ref)를 참조하십시오.

# 예제

```jldoctest
julia> v = [3, 1, 2]; sort!(v); v
3-element Vector{Int64}:
 1
 2
 3

julia> v = [3, 1, 2]; sort!(v, rev = true); v
3-element Vector{Int64}:
 3
 2
 1

julia> v = [(1, "c"), (3, "a"), (2, "b")]; sort!(v, by = x -> x[1]); v
3-element Vector{Tuple{Int64, String}}:
 (1, "c")
 (2, "b")
 (3, "a")

julia> v = [(1, "c"), (3, "a"), (2, "b")]; sort!(v, by = x -> x[2]); v
3-element Vector{Tuple{Int64, String}}:
 (3, "a")
 (2, "b")
 (1, "c")

julia> sort(0:3, by=x->x-2, order=Base.Order.By(abs)) # same as sort(0:3, by=abs(x->x-2))
4-element Vector{Int64}:
 2
 1
 3
 0

julia> sort([2, NaN, 1, NaN, 3]) # correct sort with default lt=isless
5-element Vector{Float64}:
   1.0
   2.0
   3.0
 NaN
 NaN

julia> sort([2, NaN, 1, NaN, 3], lt=<) # wrong sort due to invalid lt. This behavior is undefined.
5-element Vector{Float64}:
   2.0
 NaN
   1.0
 NaN
   3.0
```
