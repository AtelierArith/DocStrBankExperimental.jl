```
@everywhere [procs()] expr
```

모든 `procs`에서 `Main` 아래에서 표현식을 실행합니다. 프로세스 중 하나에서 발생한 오류는 [`CompositeException`](@ref)으로 수집되어 던져집니다. 예를 들어:

```
@everywhere bar = 1
```

는 모든 현재 프로세스에서 `Main.bar`를 정의합니다. 나중에 추가된 프로세스(예: [`addprocs()`](@ref)로 추가된 프로세스)에서는 표현식이 정의되지 않습니다.

[`@spawnat`](@ref)와 달리, `@everywhere`는 로컬 변수를 캡처하지 않습니다. 대신, 로컬 변수를 보간을 사용하여 브로드캐스트할 수 있습니다:

```
foo = 1
@everywhere bar = $foo
```

선택적 인수 `procs`는 표현식을 실행할 프로세스의 하위 집합을 지정할 수 있습니다.

`remotecall_eval(Main, procs, expr)`을 호출하는 것과 유사하지만 두 가지 추가 기능이 있습니다:

```
- `using` 및 `import` 문이 호출 프로세스에서 먼저 실행되어 패키지가 미리 컴파일되도록 합니다.
- `include`에 의해 사용되는 현재 소스 파일 경로가 다른 프로세스로 전파됩니다.
```
