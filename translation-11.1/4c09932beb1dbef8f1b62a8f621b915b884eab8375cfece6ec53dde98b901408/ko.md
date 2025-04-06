```
diagm(kv::Pair{<:Integer,<:AbstractVector}...)
diagm(m::Integer, n::Integer, kv::Pair{<:Integer,<:AbstractVector}...)

`Pair`의 대각선과 벡터로부터 행렬을 구성합니다. 벡터 `kv.second`는 `kv.first` 대각선에 배치됩니다. 기본적으로 행렬은 정사각형이며 그 크기는 `kv`로부터 유추되지만, 필요에 따라 0으로 패딩된 비정사각형 크기 `m`×`n`을 첫 번째 인수로 `m,n`을 전달하여 지정할 수 있습니다. 반복된 대각선 인덱스 `kv.first`에 대해 해당 벡터 `kv.second`의 값이 더해집니다.

`diagm`은 전체 행렬을 구성합니다; 저장 효율적인 버전과 빠른 산술 연산을 원하신다면 [`Diagonal`](@ref), [`Bidiagonal`](@ref), [`Tridiagonal`](@ref) 및 [`SymTridiagonal`](@ref)를 참조하세요.

# 예제

```

jldoctest julia> diagm(1 => [1,2,3]) 4×4 Matrix{Int64}:  0  1  0  0  0  0  2  0  0  0  0  3  0  0  0  0

julia> diagm(1 => [1,2,3], -1 => [4,5]) 4×4 Matrix{Int64}:  0  1  0  0  4  0  2  0  0  5  0  3  0  0  0  0

julia> diagm(1 => [1,2,3], 1 => [1,2,3]) 4×4 Matrix{Int64}:  0  2  0  0  0  0  4  0  0  0  0  6  0  0  0  0 ```
