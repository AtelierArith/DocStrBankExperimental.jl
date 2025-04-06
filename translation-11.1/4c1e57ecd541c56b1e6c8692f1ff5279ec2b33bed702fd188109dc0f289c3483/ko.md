```
cumsum(A; dims::Integer)
```

차원 `dims`에 따라 누적 합을 계산합니다. 성능을 위해 미리 할당된 출력 배열을 사용하고 출력의 정밀도를 제어하기 위해 [`cumsum!`](@ref)도 참조하십시오 (예: 오버플로우를 피하기 위해).

# 예제

```jldoctest
julia> a = [1 2 3; 4 5 6]
2×3 Matrix{Int64}:
 1  2  3
 4  5  6

julia> cumsum(a, dims=1)
2×3 Matrix{Int64}:
 1  2  3
 5  7  9

julia> cumsum(a, dims=2)
2×3 Matrix{Int64}:
 1  3   6
 4  9  15
```

!!! note
    반환 배열의 `eltype`은 시스템 단어 크기보다 작은 부호 있는 정수의 경우 `Int`이고, 시스템 단어 크기보다 작은 부호 없는 정수의 경우 `UInt`입니다. 작은 부호 있는 또는 부호 없는 정수 배열의 `eltype`을 유지하려면 `accumulate(+, A)`를 사용해야 합니다.

    ```jldoctest
    julia> cumsum(Int8[100, 28])
    2-element Vector{Int64}:
     100
     128

    julia> accumulate(+,Int8[100, 28])
    2-element Vector{Int8}:
      100
     -128
    ```

    첫 번째 경우에서 정수는 시스템 단어 크기로 확장되므로 결과는 `Int64[100, 128]`입니다. 두 번째 경우에서는 그러한 확장이 발생하지 않으며 정수 오버플로우로 인해 `Int8[100, -128]`가 됩니다.

