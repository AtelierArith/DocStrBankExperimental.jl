```
kron(A, B)
```

두 벡터, 행렬 또는 숫자의 크로네커 곱을 계산합니다.

실수 벡터 `v`와 `w`에 대해, 크로네커 곱은 외적과 관련이 있으며 `kron(v,w) == vec(w * transpose(v))` 또는 `w * transpose(v) == reshape(kron(v,w), (length(w), length(v)))`로 표현됩니다. 이러한 표현의 왼쪽과 오른쪽에서 `v`와 `w`의 순서가 다름을 주목하세요(열 우선 저장 방식 때문입니다). 복소수 벡터의 경우, 외적 `w * v'`는 `v`의 켤레에 의해 다릅니다.

# 예제

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> B = [im 1; 1 -im]
2×2 Matrix{Complex{Int64}}:
 0+1im  1+0im
 1+0im  0-1im

julia> kron(A, B)
4×4 Matrix{Complex{Int64}}:
 0+1im  1+0im  0+2im  2+0im
 1+0im  0-1im  2+0im  0-2im
 0+3im  3+0im  0+4im  4+0im
 3+0im  0-3im  4+0im  0-4im

julia> v = [1, 2]; w = [3, 4, 5];

julia> w*transpose(v)
3×2 Matrix{Int64}:
 3   6
 4   8
 5  10

julia> reshape(kron(v,w), (length(w), length(v)))
3×2 Matrix{Int64}:
 3   6
 4   8
 5  10
```
