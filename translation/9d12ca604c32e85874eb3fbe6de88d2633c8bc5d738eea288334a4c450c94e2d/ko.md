```
PersistentDict
```

`PersistentDict`는 해시 배열 매핑 트리로 구현된 사전으로, 지속성이 필요한 상황에 최적화되어 있습니다. 각 작업은 이전 것과 분리된 새로운 사전을 반환하지만, 기본 구현은 공간 효율적이며 여러 개의 별도 사전 간에 저장소를 공유할 수 있습니다.

!!! note
    IdDict처럼 동작합니다.


```julia
PersistentDict(KV::Pair)
```

# 예제

```jldoctest
julia> dict = Base.PersistentDict(:a=>1)
Base.PersistentDict{Symbol, Int64} with 1 entry:
  :a => 1

julia> dict2 = Base.delete(dict, :a)
Base.PersistentDict{Symbol, Int64}()

julia> dict3 = Base.PersistentDict(dict, :a=>2)
Base.PersistentDict{Symbol, Int64} with 1 entry:
  :a => 2
```
