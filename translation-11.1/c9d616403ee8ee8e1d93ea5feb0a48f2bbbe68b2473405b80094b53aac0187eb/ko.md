```
fetch(x::Future)
```

[`Future`](@ref)의 값을 기다리고 가져옵니다. 가져온 값은 로컬에 캐시됩니다. 동일한 참조에 대한 추가 `fetch` 호출은 캐시된 값을 반환합니다. 원격 값이 예외인 경우, 원격 예외와 백트레이스를 캡처하는 [`RemoteException`](@ref)을 발생시킵니다.
