```
keytype(type)
```

사전 유형의 키 유형을 가져옵니다. [`eltype`](@ref)와 유사하게 동작합니다.

# 예제

```jldoctest
julia> keytype(Dict(Int32(1) => "foo"))
Int32
```
