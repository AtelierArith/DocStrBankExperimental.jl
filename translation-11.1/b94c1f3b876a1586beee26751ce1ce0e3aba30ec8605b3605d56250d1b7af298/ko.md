```
RemoteException(captured)
```

원격 계산에서 발생한 예외는 캡처되어 로컬에서 다시 발생합니다. `RemoteException`은 작업자의 `pid`와 캡처된 예외를 래핑합니다. `CapturedException`은 원격 예외와 예외가 발생했을 때의 호출 스택의 직렬화 가능한 형태를 캡처합니다.
