```
unsafe_modify!(p::Ptr{T}, op, x, [order::Symbol]) -> Pair
```

이 함수는 메모리 주소를 가져오고 설정하기 위해 `op` 함수를 적용한 후 원자적으로 작업을 수행합니다. 하드웨어에서 지원하는 경우(예: 원자적 증가) 적절한 하드웨어 명령어로 최적화될 수 있으며, 그렇지 않으면 실행은 다음과 유사합니다:

```
y = unsafe_load(p)
z = op(y, x)
unsafe_store!(p, z)
return y => z
```

이 함수의 `unsafe` 접두사는 포인터 `p`가 유효한지 확인하기 위한 검증이 수행되지 않음을 나타냅니다. C와 마찬가지로, 프로그래머는 이 함수를 호출하는 동안 참조된 메모리가 해제되거나 가비지 수집되지 않도록 보장할 책임이 있습니다. 잘못된 사용은 프로그램을 세그멘테이션 오류로 만들 수 있습니다.

!!! compat "Julia 1.10"
    이 함수는 최소한 Julia 1.10이 필요합니다.


참고: [`modifyproperty!`](@ref Base.modifyproperty!), [`atomic`](@ref)
