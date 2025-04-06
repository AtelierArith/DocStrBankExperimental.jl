```
StackFrame
```

실행 컨텍스트를 나타내는 스택 정보로, 다음 필드를 포함합니다:

  * `func::Symbol`

    실행 컨텍스트를 포함하는 함수의 이름입니다.
  * `linfo::Union{Core.MethodInstance, Method, Module, Core.CodeInfo, Nothing}`

    실행 컨텍스트를 포함하는 MethodInstance 또는 CodeInfo(찾을 수 있는 경우) 또는 매크로 확장을 위한 모듈입니다.
  * `file::Symbol`

    실행 컨텍스트를 포함하는 파일의 경로입니다.
  * `line::Int`

    실행 컨텍스트를 포함하는 파일의 줄 번호입니다.
  * `from_c::Bool`

    코드가 C에서 온 경우 True입니다.
  * `inlined::Bool`

    코드가 인라인 프레임에서 온 경우 True입니다.
  * `pointer::UInt64`

    `backtrace`에 의해 반환된 실행 컨텍스트에 대한 포인터의 표현입니다.
