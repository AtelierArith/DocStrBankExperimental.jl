```
invpermute!(v, p)
```

[`permute!`](@ref)와 유사하지만, 주어진 순열의 역이 적용됩니다.

미리 할당된 출력 배열이 있는 경우(예: `u = similar(v)`), 대신 `u[p] = v`를 사용하는 것이 더 빠릅니다. (`invpermute!`는 내부적으로 데이터의 복사본을 할당합니다.)

!!! 경고     변형된 인수가 다른 인수와 메모리를 공유할 경우 예상치 못한 동작이 발생할 수 있습니다.

# 예제

```jldoctest
julia> A = [1, 1, 3, 4];

julia> perm = [2, 4, 3, 1];

julia> invpermute!(A, perm);

julia> A
4-element Vector{Int64}:
 4
 1
 3
 1
```
