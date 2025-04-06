```
open(f::Function, command, args...; kwargs...)
```

`open(command, args...; kwargs...)`와 유사하지만, 결과 프로세스 스트림에서 `f(stream)`을 호출한 다음 입력 스트림을 닫고 프로세스가 완료될 때까지 기다립니다. 성공 시 `f`가 반환한 값을 반환합니다. 프로세스가 실패하거나 프로세스가 stdout에 무엇이든 출력하려고 시도하면 오류를 발생시킵니다.
