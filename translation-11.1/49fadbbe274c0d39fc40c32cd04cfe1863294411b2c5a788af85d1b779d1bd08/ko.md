```
Base.Pairs(values, keys) <: AbstractDict{eltype(keys), eltype(values)}
```

인덱스 가능한 컨테이너를 동일한 데이터의 사전 뷰로 변환합니다. 기본 데이터의 키 공간을 수정하면 이 객체가 무효화될 수 있습니다.
