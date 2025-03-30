```
Threads.maxthreadid() -> Int
```

Julia 프로세스에서 사용 가능한 스레드 수(모든 스레드 풀에 걸쳐)에 대한 하한을 가져옵니다. 원자적 획득 의미론을 사용합니다. 결과는 항상 [`threadid()`](@ref) 및 `threadid(task)`보다 크거나 같으며, 이는 `maxthreadid`를 호출하기 전에 관찰할 수 있었던 모든 작업에 해당합니다.
