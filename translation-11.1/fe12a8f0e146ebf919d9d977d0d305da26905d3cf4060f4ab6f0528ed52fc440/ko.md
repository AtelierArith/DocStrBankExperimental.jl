```
GC.safepoint()
```

프로그램에서 가비지 수집이 실행될 수 있는 지점을 삽입합니다. 이는 일부 스레드가 메모리를 할당하고 (따라서 GC를 실행해야 할 수 있는) 반면, 다른 스레드는 단순한 작업만 수행하는 멀티 스레드 프로그램에서 드문 경우에 유용할 수 있습니다 (할당, 작업 전환 또는 I/O 없음). 비할당 스레드에서 이 함수를 주기적으로 호출하면 가비지 수집이 실행될 수 있습니다.

!!! compat "Julia 1.4"
    이 함수는 Julia 1.4부터 사용할 수 있습니다.

