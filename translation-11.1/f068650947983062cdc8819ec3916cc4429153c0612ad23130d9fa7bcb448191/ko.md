```
Timer(callback::Function, delay; interval = 0)
```

함수를 `callback`으로 설정하여 타이머 만료 시마다 실행되는 타이머를 생성합니다.

대기 중인 작업이 깨어나고 함수 `callback`은 초기 지연 시간 `delay` 초 후에 호출되며, 이후 주어진 간격 `interval` 초마다 반복됩니다. `interval`이 `0`이면 콜백은 한 번만 실행됩니다. 함수 `callback`은 타이머 자체를 단일 인수로 사용하여 호출됩니다. `close`를 호출하여 타이머를 중지합니다. 타이머가 이미 만료된 경우 콜백이 마지막으로 한 번 더 실행될 수 있습니다.

# 예제

여기서 첫 번째 숫자는 2초의 지연 후에 출력되고, 그 다음 숫자는 빠르게 출력됩니다.

```julia-repl
julia> begin
           i = 0
           cb(timer) = (global i += 1; println(i))
           t = Timer(cb, 2, interval=0.2)
           wait(t)
           sleep(0.5)
           close(t)
       end
1
2
3
```
