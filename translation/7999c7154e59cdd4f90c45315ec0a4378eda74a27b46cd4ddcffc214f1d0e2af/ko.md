```
isready(rr::RemoteChannel, args...)
```

[`RemoteChannel`](@ref)에 값이 저장되어 있는지 확인합니다. 이 함수는 결과를 받을 때까지 시간이 걸리기 때문에 경쟁 조건이 발생할 수 있습니다. 그러나 [`Future`](@ref)에서는 한 번만 할당되므로 안전하게 사용할 수 있습니다.
