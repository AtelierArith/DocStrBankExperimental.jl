```
clear_malloc_data()
```

`--track-allocation` 옵션으로 Julia를 실행할 때 저장된 메모리 할당 데이터를 지웁니다. 테스트할 명령어를 실행하여 JIT 컴파일을 강제한 다음, [`clear_malloc_data`](@ref)를 호출합니다. 그런 다음 명령어를 다시 실행하고, Julia를 종료한 후 결과 `*.mem` 파일을 검사합니다.
