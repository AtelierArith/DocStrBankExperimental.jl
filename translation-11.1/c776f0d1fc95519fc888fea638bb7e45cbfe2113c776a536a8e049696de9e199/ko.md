```
isabstracttype(T)
```

타입 `T`가 추상 타입으로 선언되었는지 (즉, `abstract type` 구문을 사용하여) 확인합니다. 이는 `isconcretetype(T)`의 부정이 아님에 유의하십시오. 만약 `T`가 타입이 아니라면 `false`를 반환합니다.

# 예시

```jldoctest
julia> isabstracttype(AbstractArray)
true

julia> isabstracttype(Vector)
false
```
