```
RemoteChannel(pid::Integer=myid())
```

프로세스 `pid`에서 `Channel{Any}(1)`에 대한 참조를 만듭니다. 기본 `pid`는 현재 프로세스입니다.

```
RemoteChannel(f::Function, pid::Integer=myid())
```

특정 크기와 유형의 원격 채널에 대한 참조를 생성합니다. `f`는 `pid`에서 실행될 때 `AbstractChannel`의 구현을 반환해야 하는 함수입니다.

예를 들어, `RemoteChannel(()->Channel{Int}(10), pid)`는 `pid`에서 유형 `Int`와 크기 10의 채널에 대한 참조를 반환합니다.

기본 `pid`는 현재 프로세스입니다.
