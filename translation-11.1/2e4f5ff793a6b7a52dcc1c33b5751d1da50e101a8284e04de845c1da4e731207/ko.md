```
edit(function, [types])
edit(module)
```

함수의 정의를 편집하며, 선택적으로 어떤 메서드를 편집할지 나타내기 위해 타입의 튜플을 지정할 수 있습니다. 모듈의 경우, 주요 소스 파일을 엽니다. 모듈은 먼저 `using` 또는 `import`로 로드되어야 합니다.

!!! compat "Julia 1.1"
    모듈에 대한 `edit`는 최소한 Julia 1.1이 필요합니다.


주어진 줄에서 파일을 열 수 있도록 하려면, 먼저 `InteractiveUtils.define_editor`를 호출해야 할 수 있습니다.
