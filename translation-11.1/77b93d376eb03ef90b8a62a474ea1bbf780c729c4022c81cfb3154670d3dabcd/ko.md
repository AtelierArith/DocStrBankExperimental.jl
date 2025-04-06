```
partialsortperm!(ix, v, k; by=identity, lt=isless, rev=false)
```

[`partialsortperm`](@ref)와 유사하지만, `v`와 동일한 크기의 미리 할당된 인덱스 벡터 `ix`를 받아들이며, 이는 `v`의 인덱스(순열)를 저장하는 데 사용됩니다.

`ix`는 `v`의 인덱스를 포함하도록 초기화됩니다.

(일반적으로 `v`의 인덱스는 `1:length(v)`이지만, `v`가 `OffsetArray`와 같이 비기본 인덱스를 가진 대체 배열 유형인 경우, `ix`는 동일한 인덱스를 공유해야 합니다.)

반환 시, `ix`는 정렬된 위치에 `k`의 인덱스를 가지도록 보장되며, 다음과 같은 관계가 성립합니다.

```julia
partialsortperm!(ix, v, k);
v[ix[k]] == partialsort(v, k)
```

반환 값은 `k`가 정수인 경우 `ix`의 `k`번째 요소이며, `k`가 범위인 경우 `ix`에 대한 뷰입니다.

!!! 경고     변형된 인수가 다른 인수와 메모리를 공유할 경우 동작이 예기치 않게 될 수 있습니다.

# 예제

```jldoctest
julia> v = [3, 1, 2, 1];

julia> ix = Vector{Int}(undef, 4);

julia> partialsortperm!(ix, v, 1)
2

julia> ix = [1:4;];

julia> partialsortperm!(ix, v, 2:3)
2-element view(::Vector{Int64}, 2:3) with eltype Int64:
 4
 3
```

```
