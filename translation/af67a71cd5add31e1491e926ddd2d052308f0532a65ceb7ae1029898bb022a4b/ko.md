```
transpose!(dest,src)
```

배열 `src`를 전치하고 결과를 미리 할당된 배열 `dest`에 저장합니다. `dest`의 크기는 `(size(src,2),size(src,1))`에 해당해야 합니다. 제자리 전치는 지원되지 않으며, `src`와 `dest`가 겹치는 메모리 영역을 가지면 예기치 않은 결과가 발생할 수 있습니다.

# 예제

```jldoctest
julia> A = [3+2im 9+2im; 8+7im  4+6im]
2×2 Matrix{Complex{Int64}}:
 3+2im  9+2im
 8+7im  4+6im

julia> B = zeros(Complex{Int64}, 2, 2)
2×2 Matrix{Complex{Int64}}:
 0+0im  0+0im
 0+0im  0+0im

julia> transpose!(B, A);

julia> B
2×2 Matrix{Complex{Int64}}:
 3+2im  8+7im
 9+2im  4+6im

julia> A
2×2 Matrix{Complex{Int64}}:
 3+2im  9+2im
 8+7im  4+6im
```
