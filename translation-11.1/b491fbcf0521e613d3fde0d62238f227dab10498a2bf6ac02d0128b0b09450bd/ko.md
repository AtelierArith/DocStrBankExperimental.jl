```
logdet(M)
```

행렬 행렬식의 로그. `log(det(M))`와 동등하지만, 정확성을 높이고 오버플로우/언더플로우를 피할 수 있습니다.

# 예제

```jldoctest
julia> M = [1 0; 2 2]
2×2 Matrix{Int64}:
 1  0
 2  2

julia> logdet(M)
0.6931471805599453

julia> logdet(Matrix(I, 3, 3))
0.0
```
