```
circshift!(dest, src, shifts)
```

`src`의 데이터를 원형으로 이동(회전)하여 결과를 `dest`에 저장합니다. `shifts`는 각 차원에서 이동할 양을 지정합니다.

!!! warning
    변경된 인수가 다른 인수와 메모리를 공유할 때 동작이 예기치 않게 나타날 수 있습니다.


자세한 내용은 [`circshift`](@ref)를 참조하세요.
