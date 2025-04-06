```
permutedims!(dest, src, perm)
```

배열 `src`의 차원을 변경하고 결과를 배열 `dest`에 저장합니다. `perm`은 길이가 `ndims(src)`인 순열을 지정하는 벡터입니다. 미리 할당된 배열 `dest`는 `size(dest) == size(src)[perm]`이어야 하며 완전히 덮어씌워집니다. 제자리에서의 순열은 지원되지 않으며 `src`와 `dest`가 겹치는 메모리 영역을 가지면 예기치 않은 결과가 발생합니다.

자세한 내용은 [`permutedims`](@ref)를 참조하세요.
