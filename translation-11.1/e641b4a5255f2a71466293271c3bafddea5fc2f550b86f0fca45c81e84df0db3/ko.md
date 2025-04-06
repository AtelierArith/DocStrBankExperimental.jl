```
randsubseq([rng=default_rng(),] A, p) -> Vector
```

주어진 배열 `A`의 무작위 부분 수열로 구성된 벡터를 반환합니다. 여기서 `A`의 각 요소는 독립 확률 `p`로 포함됩니다(순서대로). (복잡도는 `p*length(A)`에 선형적이므로, 이 함수는 `p`가 작고 `A`가 클 때도 효율적입니다.) 기술적으로 이 과정은 `A`의 "베르누이 샘플링"으로 알려져 있습니다.

# 예제

```jldoctest
julia> randsubseq(Xoshiro(123), 1:8, 0.3)
2-element Vector{Int64}:
 4
 7
```
