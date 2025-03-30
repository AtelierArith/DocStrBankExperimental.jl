```
Base.runtests(tests=["all"]; ncores=ceil(Int, Sys.CPU_THREADS / 2),
              exit_on_error=false, revise=false, [seed])
```

`tests`에 나열된 Julia 단위 테스트를 실행합니다. `tests`는 문자열 또는 문자열 배열일 수 있으며, `ncores` 프로세서를 사용합니다. `exit_on_error`가 `false`인 경우, 하나의 테스트가 실패하더라도 다른 파일의 나머지 테스트는 여전히 실행됩니다. 그렇지 않으면 `exit_on_error == true`일 때는 무시됩니다. `revise`가 `true`인 경우, 테스트를 실행하기 전에 `Base` 또는 표준 라이브러리에 대한 수정 사항을 로드하기 위해 `Revise` 패키지가 사용됩니다. 키워드 인수로 시드가 제공되면, 테스트가 실행되는 컨텍스트에서 전역 RNG의 시드로 사용됩니다. 그렇지 않으면 시드는 무작위로 선택됩니다.
