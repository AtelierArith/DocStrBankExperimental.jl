```
setindex!(collection, value, key...)
```

주어진 값(value)을 컬렉션 내의 주어진 키(key) 또는 인덱스(index)에 저장합니다. 구문 `a[i,j,...] = x`는 컴파일러에 의해 `(setindex!(a, x, i, j, ...); x)`로 변환됩니다.

# 예제

```jldoctest
julia> a = Dict("a"=>1)
Dict{String, Int64} with 1 entry:
  "a" => 1

julia> setindex!(a, 2, "b")
Dict{String, Int64} with 2 entries:
  "b" => 2
  "a" => 1
```
