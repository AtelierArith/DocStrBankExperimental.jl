```
handle_message(logger, level, message, _module, group, id, file, line; key1=val1, ...)
```

`logger`에 `level`로 메시지를 기록합니다. 메시지가 생성된 논리적 위치는 모듈 `_module`과 `group`에 의해 제공되며, 소스 위치는 `file`과 `line`에 의해 제공됩니다. `id`는 필터링할 때 로그 문을 식별하는 키로 사용되는 임의의 고유 값(일반적으로 [`Symbol`](@ref))입니다.
