```
timedwait(testcb, timeout::Real; pollint::Real=0.1)
```

`testcb()`가 `true`를 반환하거나 `timeout` 초가 경과할 때까지 기다립니다. 두 경우 중 더 이른 경우에 종료됩니다. 테스트 함수는 매 `pollint` 초마다 폴링됩니다. `pollint`의 최소값은 0.001초, 즉 1밀리초입니다.

`:ok` 또는 `:timed_out`을 반환합니다.

# 예제

```jldoctest
julia> cb() = (sleep(5); return);

julia> t = @async cb();

julia> timedwait(()->istaskdone(t), 1)
:timed_out

julia> timedwait(()->istaskdone(t), 6.5)
:ok
```
