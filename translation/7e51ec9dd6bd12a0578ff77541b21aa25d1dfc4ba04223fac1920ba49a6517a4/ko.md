```
@arg_test arg1 arg2 ... body
```

`@arg_test` 매크로는 `arg_readers`와 `arg_writers`에서 제공하는 `arg` 함수를 실제 인수 값으로 변환하는 데 사용됩니다. `@arg_test arg body`를 작성하면 `arg(arg -> body)`와 동일합니다.
