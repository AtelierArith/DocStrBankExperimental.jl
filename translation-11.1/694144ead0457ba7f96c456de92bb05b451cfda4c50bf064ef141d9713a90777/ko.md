```
pairs(IndexLinear(), A)
pairs(IndexCartesian(), A)
pairs(IndexStyle(A), A)
```

배열 `A`의 각 요소에 접근하는 반복자로, `i => x`를 반환합니다. 여기서 `i`는 요소의 인덱스이고 `x = A[i]`입니다. `pairs(A)`와 동일하지만 인덱스 스타일을 선택할 수 있습니다. 또한 `enumerate(A)`와 유사하지만, `i`는 `A`의 유효한 인덱스가 되며, `enumerate`는 항상 1부터 세기 때문에 `A`의 인덱스와는 관계가 없습니다.

[`IndexLinear()`](@ref)를 지정하면 `i`가 정수가 되도록 보장합니다. [`IndexCartesian()`](@ref)를 지정하면 `i`가 [`Base.CartesianIndex`](@ref)가 되도록 보장합니다. `IndexStyle(A)`를 지정하면 배열 `A`의 기본 인덱싱 스타일로 정의된 것을 선택합니다.

기본 배열의 경계를 변경하면 이 반복자는 무효화됩니다.

# 예제

```jldoctest
julia> A = ["a" "d"; "b" "e"; "c" "f"];

julia> for (index, value) in pairs(IndexStyle(A), A)
           println("$index $value")
       end
1 a
2 b
3 c
4 d
5 e
6 f

julia> S = view(A, 1:2, :);

julia> for (index, value) in pairs(IndexStyle(S), S)
           println("$index $value")
       end
CartesianIndex(1, 1) a
CartesianIndex(2, 1) b
CartesianIndex(1, 2) d
CartesianIndex(2, 2) e
```

자세한 내용은 [`IndexStyle`](@ref), [`axes`](@ref)를 참조하세요.
