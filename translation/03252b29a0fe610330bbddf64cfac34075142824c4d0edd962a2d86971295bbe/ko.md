```
PermutedDimsArray(A, perm) -> B
```

주어진 AbstractArray `A`에 대해, 차원이 순서가 바뀐 것처럼 보이는 뷰 `B`를 생성합니다. `permutedims`와 유사하지만, 복사가 발생하지 않으며 (`B`는 `A`와 저장소를 공유합니다).

자세한 내용은 [`permutedims`](@ref), [`invperm`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> A = rand(3,5,4);

julia> B = PermutedDimsArray(A, (3,1,2));

julia> size(B)
(4, 3, 5)

julia> B[3,1,2] == A[1,2,3]
true
```
