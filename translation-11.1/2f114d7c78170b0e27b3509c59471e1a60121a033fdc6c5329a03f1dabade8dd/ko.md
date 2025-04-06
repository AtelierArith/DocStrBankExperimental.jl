```
islocked(lock) -> 상태 (부울)
```

`lock`이 어떤 작업/스레드에 의해 보유되고 있는지 확인합니다. 이 함수는 단독으로 동기화에 사용되어서는 안 됩니다. 그러나 `islocked`와 [`trylock`](@ref)를 결합하면 *`typeof(lock)`*에 의해 지원되는 경우 테스트-테스트-세트 또는 지수 백오프 알고리즘을 작성하는 데 사용할 수 있습니다(문서를 참조하십시오).

# 확장 도움말

예를 들어, `lock` 구현이 아래에 문서화된 속성을 만족하는 경우 지수 백오프를 다음과 같이 구현할 수 있습니다.

```julia
nspins = 0
while true
    while islocked(lock)
        GC.safepoint()
        nspins += 1
        nspins > LIMIT && error("timeout")
    end
    trylock(lock) && break
    backoff()
end
```

## 구현

잠금 구현은 다음 속성으로 `islocked`를 정의하고 이를 문서 문자열에 명시하는 것이 좋습니다.

  * `islocked(lock)`은 데이터 경합이 없습니다.
  * `islocked(lock)`이 `false`를 반환하면, 다른 작업의 간섭이 없을 경우 `trylock(lock)`의 즉각적인 호출이 성공해야 합니다( `true`를 반환).
