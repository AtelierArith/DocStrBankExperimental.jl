```
Base.summarysize(obj; exclude=Union{...}, chargeall=Union{...}) -> Int
```

인수에서 도달 가능한 모든 고유 객체가 사용하는 메모리 양(바이트 단위)을 계산합니다.

# 키워드 인수

  * `exclude`: 탐색에서 제외할 객체의 유형을 지정합니다.
  * `chargeall`: 일반적으로 제외되는 필드라도 항상 모든 필드의 크기를 계산할 객체의 유형을 지정합니다.

자세한 내용은 [`sizeof`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> Base.summarysize(1.0)
8

julia> Base.summarysize(Ref(rand(100)))
848

julia> sizeof(Ref(rand(100)))
8
```
