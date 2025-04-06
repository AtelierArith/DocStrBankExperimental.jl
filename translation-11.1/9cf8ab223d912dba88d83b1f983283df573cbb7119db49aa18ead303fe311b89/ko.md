```
@test_logs [log_patterns...] [keywords] 표현식
```

`collect_test_logs`를 사용하여 `표현식`에 의해 생성된 로그 레코드 목록을 수집하고, 이들이 `log_patterns` 시퀀스와 일치하는지 확인한 후 `표현식`의 값을 반환합니다. `keywords`는 로그 레코드의 간단한 필터링을 제공합니다: `min_level` 키워드는 테스트를 위해 수집될 최소 로그 수준을 제어하고, `match_mode` 키워드는 매칭이 어떻게 수행될지를 정의합니다(기본값 `:all`은 모든 로그와 패턴이 쌍으로 일치하는지 확인합니다; `:any`를 사용하여 패턴이 시퀀스의 어딘가에서 최소한 한 번 일치하는지 확인합니다).

가장 유용한 로그 패턴은 `(level,message)` 형식의 간단한 튜플입니다. 다른 수의 튜플 요소를 사용하여 `AbstractLogger`에 `handle_message` 함수를 통해 전달된 인수에 해당하는 다른 로그 메타데이터와 일치시킬 수 있습니다: `(level,message,module,group,id,file,line)`. 존재하는 요소는 기본적으로 `==`를 사용하여 로그 레코드 필드와 쌍으로 일치하며, `Symbol`은 표준 로그 수준에 사용할 수 있고, 패턴의 `Regex`는 문자열 또는 `Symbol` 필드를 `occursin`을 사용하여 일치시킵니다.

# 예제

경고를 기록하고 여러 디버그 메시지를 기록하는 함수를 고려해 보겠습니다:

```
function foo(n)
    @info "Doing foo with n=$n"
    for i=1:n
        @debug "Iteration $i"
    end
    42
end
```

정보 메시지를 테스트할 수 있습니다:

```
@test_logs (:info,"Doing foo with n=2") foo(2)
```

디버그 메시지도 테스트하고 싶다면, `min_level` 키워드로 이를 활성화해야 합니다:

```
using Logging
@test_logs (:info,"Doing foo with n=2") (:debug,"Iteration 1") (:debug,"Iteration 2") min_level=Logging.Debug foo(2)
```

특정 메시지가 생성되는지 테스트하고 나머지는 무시하고 싶다면, `match_mode=:any` 키워드를 설정할 수 있습니다:

```
using Logging
@test_logs (:info,) (:debug,"Iteration 42") min_level=Logging.Debug match_mode=:any foo(100)
```

매크로는 반환된 값을 테스트하기 위해 `@test`와 함께 연결할 수 있습니다:

```
@test (@test_logs (:info,"Doing foo with n=2") foo(2)) == 42
```

경고가 없는지 테스트하고 싶다면 로그 패턴을 지정하지 않고 `min_level`을 적절히 설정할 수 있습니다:

```
# 로거 수준이 warn일 때 표현식이 메시지를 기록하지 않는지 테스트:
@test_logs min_level=Logging.Warn @info("Some information") # 통과
@test_logs min_level=Logging.Warn @warn("Some information") # 실패
```

`@warn`에 의해 생성되지 않은 [`stderr`](@ref)에서 경고(또는 오류 메시지)의 부재를 테스트하려면 [`@test_nowarn`](@ref)을 참조하십시오. ```
