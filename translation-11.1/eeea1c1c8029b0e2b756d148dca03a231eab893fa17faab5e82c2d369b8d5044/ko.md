```
SparseVector{Tv,Ti<:Integer} <: AbstractSparseVector{Tv,Ti}
```

희소 벡터를 저장하기 위한 벡터 유형입니다. 벡터의 길이, *정렬된* 비영(非零) 인덱스 벡터, 비영(非零) 값 벡터를 전달하여 생성할 수 있습니다.

예를 들어, 벡터 `[5, 6, 0, 7]`는 다음과 같이 표현할 수 있습니다.

```julia
SparseVector(4, [1, 2, 4], [5, 6, 7])
```

이는 인덱스 1의 요소가 5, 인덱스 2의 요소가 6, 인덱스 3의 요소가 `zero(Int)`, 인덱스 4의 요소가 7임을 나타냅니다.

`dense` 벡터에서 직접 희소 벡터를 생성하는 것이 더 편리할 수 있으며, `sparse`를 사용하여 다음과 같이 할 수 있습니다.

```julia
sparse([5, 6, 0, 7])
```

이는 동일한 희소 벡터를 생성합니다.
