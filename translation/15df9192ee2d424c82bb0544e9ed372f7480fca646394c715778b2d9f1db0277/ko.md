```
unsafe_replace!(p::Ptr{T}, expected, desired,
               [success_order::Symbol[, fail_order::Symbol=success_order]]) -> (; old, success::Bool)
```

이 함수는 메모리 주소를 주어진 값으로 조건부로 설정하고 가져오는 작업을 원자적으로 수행합니다. 하드웨어에서 지원하는 경우, 이는 적절한 하드웨어 명령어로 최적화될 수 있으며, 그렇지 않으면 실행은 다음과 유사합니다:

```
y = unsafe_load(p, fail_order)
ok = y === expected
if ok
    unsafe_store!(p, desired, success_order)
end
return (; old = y, success = ok)
```

이 함수의 `unsafe` 접두사는 포인터 `p`가 유효한지 확인하기 위한 검증이 수행되지 않음을 나타냅니다. C와 마찬가지로, 프로그래머는 이 함수를 호출하는 동안 참조된 메모리가 해제되거나 가비지 수집되지 않도록 보장할 책임이 있습니다. 잘못된 사용은 프로그램을 세그멘테이션 오류로 만들 수 있습니다.

!!! compat "Julia 1.10"
    이 함수는 최소한 Julia 1.10이 필요합니다.


참고: [`replaceproperty!`](@ref Base.replaceproperty!), [`atomic`](@ref)
