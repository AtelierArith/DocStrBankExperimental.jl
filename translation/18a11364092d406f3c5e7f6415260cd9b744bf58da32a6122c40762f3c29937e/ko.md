```
systemsleep(s::Real)
```

`s` 초 동안 실행을 중단합니다. 이 함수는 Julia의 스케줄러에 양보하지 않으므로, 수면 시간 동안 실행 중인 Julia 스레드를 차단합니다.

또한 [`sleep`](@ref)를 참조하세요.
