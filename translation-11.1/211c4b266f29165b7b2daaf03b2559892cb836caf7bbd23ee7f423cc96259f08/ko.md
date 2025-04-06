```
elsize(type)
```

주어진 `type` 내에 저장된 [`eltype`](@ref) 요소 간의 메모리 스트라이드를 바이트 단위로 계산합니다. 배열 요소가 균일한 선형 스트라이드로 조밀하게 저장되는 경우입니다.

# 예제

```jldoctest
julia> Base.elsize(rand(Float32, 10))
4
```
