```
put!(rr::Future, v)
```

값을 [`Future`](@ref) `rr`에 저장합니다. `Future`는 한 번만 쓸 수 있는 원격 참조입니다. 이미 설정된 `Future`에 대해 `put!`을 호출하면 `Exception`이 발생합니다. 모든 비동기 원격 호출은 `Future`를 반환하며, 완료 시 호출의 반환 값으로 값을 설정합니다.
