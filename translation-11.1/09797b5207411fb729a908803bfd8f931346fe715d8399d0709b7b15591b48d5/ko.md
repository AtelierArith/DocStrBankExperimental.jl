```
stack(f, args...; [dims])
```

컬렉션의 각 요소에 함수를 적용하고 결과를 `stack`합니다. 또는 여러 컬렉션을 [`zip`](@ref)하여 함께 사용할 수 있습니다.

함수는 모두 같은 크기의 배열(또는 튜플, 또는 다른 반복자)을 반환해야 합니다. 이들은 결과의 슬라이스가 되며, 주어진 경우 `dims`를 따라 또는 기본적으로 마지막 차원을 따라 구분됩니다.

또한 [`mapslices`](@ref), [`eachcol`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> stack(c -> (c, c-32), "julia")
2×5 Matrix{Char}:
 'j'  'u'  'l'  'i'  'a'
 'J'  'U'  'L'  'I'  'A'

julia> stack(eachrow([1 2 3; 4 5 6]), (10, 100); dims=1) do row, n
         vcat(row, row .* n, row ./ n)
       end
2×9 Matrix{Float64}:
 1.0  2.0  3.0   10.0   20.0   30.0  0.1   0.2   0.3
 4.0  5.0  6.0  400.0  500.0  600.0  0.04  0.05  0.06
```
