```
SubArray{T,N,P,I,L} <: AbstractArray{T,N}
```

`N`-차원 부모 배열(유형 `P`)에 대한 뷰로, 요소 유형 `T`를 가지며, 인덱스 튜플(유형 `I`)로 제한됩니다. `L`은 빠른 선형 인덱싱을 지원하는 유형에 대해 true이고, 그렇지 않은 경우 false입니다.

[`view`](@ref) 함수를 사용하여 `SubArray`를 생성합니다.
