```
hvncat(dim::Int, row_first, values...)
hvncat(dims::Tuple{Vararg{Int}}, row_first, values...)
hvncat(shape::Tuple{Vararg{Tuple}}, row_first, values...)
```

여러 `values`를 한 번의 호출로 수평, 수직 및 n차원으로 연결합니다.

이 함수는 블록 행렬 구문에 대해 호출됩니다. 첫 번째 인수는 `hvcat`과 유사하게 연결의 모양을 지정하는 튜플의 튜플이거나 각 축을 따라 요소의 주요 수를 지정하는 차원으로, 출력 차원을 결정하는 데 사용됩니다. `dims` 형식은 성능이 더 좋으며, 연결 작업이 각 축을 따라 동일한 수의 요소를 가질 때 기본적으로 사용됩니다(예: [a b; c d;;; e f ; g h]). `shape` 형식은 각 축을 따라 요소의 수가 불균형할 때 사용됩니다(예: [a b ; c]). 불균형 구문은 추가 검증 오버헤드가 필요합니다. `dim` 형식은 단일 차원에 따라 연결하기 위한 최적화입니다. `row_first`는 `values`의 순서를 나타냅니다. `shape`의 첫 번째 및 두 번째 요소의 의미는 `row_first`에 따라 바뀝니다.

# 예제

```jldoctest
julia> a, b, c, d, e, f = 1, 2, 3, 4, 5, 6
(1, 2, 3, 4, 5, 6)

julia> [a b c;;; d e f]
1×3×2 Array{Int64, 3}:
[:, :, 1] =
 1  2  3

[:, :, 2] =
 4  5  6

julia> hvncat((2,1,3), false, a,b,c,d,e,f)
2×1×3 Array{Int64, 3}:
[:, :, 1] =
 1
 2

[:, :, 2] =
 3
 4

[:, :, 3] =
 5
 6

julia> [a b;;; c d;;; e f]
1×2×3 Array{Int64, 3}:
[:, :, 1] =
 1  2

[:, :, 2] =
 3  4

[:, :, 3] =
 5  6

julia> hvncat(((3, 3), (3, 3), (6,)), true, a, b, c, d, e, f)
1×3×2 Array{Int64, 3}:
[:, :, 1] =
 1  2  3

[:, :, 2] =
 4  5  6
```

# 인수 구성 예제

```
[a b c ; d e f ;;;
 g h i ; j k l ;;;
 m n o ; p q r ;;;
 s t u ; v w x]
⇒ dims = (2, 3, 4)

[a b ; c ;;; d ;;;;]
 ___   _     _
 2     1     1 = 각 행의 요소 (2, 1, 1)
 _______     _
 3           1 = 각 열의 요소 (3, 1)
 _____________
 4             = 각 3d 슬라이스의 요소 (4,)
 _____________
 4             = 각 4d 슬라이스의 요소 (4,)
⇒ shape = ((2, 1, 1), (3, 1), (4,), (4,)) with `row_first` = true
```
