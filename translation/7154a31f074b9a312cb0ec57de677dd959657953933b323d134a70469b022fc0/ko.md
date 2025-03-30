```
poll_file(path::AbstractString, interval_s::Real=5.007, timeout_s::Real=-1) -> (previous::StatStruct, current)
```

파일의 변경 사항을 모니터링하기 위해 `interval_s` 초마다 폴링하여 변경 사항이 발생하거나 `timeout_s` 초가 경과할 때까지 대기합니다. `interval_s`는 긴 기간이어야 하며, 기본값은 5.007초입니다.

변경 사항이 감지되면 상태 객체 쌍 `(previous, current)`를 반환합니다. `previous` 상태는 항상 `StatStruct`이지만, 모든 필드가 0으로 설정되어 있을 수 있습니다(파일이 이전에 존재하지 않았거나 접근할 수 없었음을 나타냄).

`current` 상태 객체는 `StatStruct`, `EOFError`(타임아웃이 경과했음을 나타냄) 또는 다른 `Exception` 하위 유형일 수 있습니다(예: `stat` 작업이 실패한 경우 - 경로가 존재하지 않는 경우 등).

파일이 수정된 시점을 확인하려면 `current isa StatStruct && mtime(prev) != mtime(current)`를 비교하여 변경 사항 알림을 감지합니다. 그러나 이 작업에는 [`watch_file`](@ref)를 사용하는 것이 더 신뢰할 수 있고 효율적이므로 선호됩니다. 다만, 일부 상황에서는 사용할 수 없을 수 있습니다.
