```
conj!(A)
```

배열을 제자리에서 복소수 켤레로 변환합니다.

자세한 내용은 [`conj`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> A = [1+im 2-im; 2+2im 3+im]
2×2 Matrix{Complex{Int64}}:
 1+1im  2-1im
 2+2im  3+1im

julia> conj!(A);

julia> A
2×2 Matrix{Complex{Int64}}:
 1-1im  2+1im
 2-2im  3-1im
```
