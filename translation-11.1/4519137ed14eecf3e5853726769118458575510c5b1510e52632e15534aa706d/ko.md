```
isequal(x, y) -> Bool
```

[`==`](@ref)와 유사하지만 부동 소수점 숫자와 결측값 처리에서 다릅니다. `isequal`은 모든 부동 소수점 `NaN` 값을 서로 같다고 간주하고, `-0.0`을 `0.0`과 다르다고 간주하며, [`missing`](@ref)을 `missing`과 같다고 간주합니다. 항상 `Bool` 값을 반환합니다.

`isequal`은 동치 관계입니다 - 반사적(`===`는 `isequal`을 의미함), 대칭적(`isequal(a, b)`는 `isequal(b, a)`를 의미함) 및 추이적(`isequal(a, b)`와 `isequal(b, c)`는 `isequal(a, c)`를 의미함)입니다.

# 구현

`isequal`의 기본 구현은 `==`를 호출하므로, 부동 소수점 값을 포함하지 않는 타입은 일반적으로 `==`만 정의하면 됩니다.

`isequal`은 해시 테이블(`Dict`)에서 사용되는 비교 함수입니다. `isequal(x,y)`는 `hash(x) == hash(y)`를 의미해야 합니다.

이는 일반적으로 사용자 정의 `==` 또는 `isequal` 메서드가 존재하는 타입이 해당하는 [`hash`](@ref) 메서드를 구현해야 함을 의미합니다(그리고 그 반대도 마찬가지입니다). 컬렉션은 일반적으로 모든 내용에 대해 `isequal`을 재귀적으로 호출하여 `isequal`을 구현합니다.

또한, `isequal`은 [`isless`](@ref)와 연결되어 있으며, 이들은 함께 고정된 총 순서를 정의하는 데 작용합니다. 여기서 `isequal(x, y)`, `isless(x, y)`, 또는 `isless(y, x)` 중 정확히 하나는 `true`여야 하며(다른 두 개는 `false`여야 함) 합니다.

스칼라 타입은 일반적으로 `==`와 별도로 `isequal`을 구현할 필요가 없지만, 더 효율적인 구현이 가능한 부동 소수점 숫자를 나타내는 경우에는 예외입니다(기본 제공되는 일반적인 대체 구현을 기반으로 `isnan`, `signbit`, 및 `==` 사용).

# 예제

```jldoctest
julia> isequal([1., NaN], [1., NaN])
true

julia> [1., NaN] == [1., NaN]
false

julia> 0.0 == -0.0
true

julia> isequal(0.0, -0.0)
false

julia> missing == missing
missing

julia> isequal(missing, missing)
true
```
