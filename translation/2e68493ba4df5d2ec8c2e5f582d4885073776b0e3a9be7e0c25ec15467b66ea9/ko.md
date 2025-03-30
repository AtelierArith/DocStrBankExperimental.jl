```
getindex(collection, key...)
```

주어진 키 또는 인덱스에 저장된 값들을 컬렉션에서 검색합니다. 구문 `a[i,j,...]`는 컴파일러에 의해 `getindex(a, i, j, ...)`로 변환됩니다.

또한 [`get`](@ref), [`keys`](@ref), [`eachindex`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> A = Dict("a" => 1, "b" => 2)
Dict{String, Int64} with 2 entries:
  "b" => 2
  "a" => 1

julia> getindex(A, "a")
1
```
