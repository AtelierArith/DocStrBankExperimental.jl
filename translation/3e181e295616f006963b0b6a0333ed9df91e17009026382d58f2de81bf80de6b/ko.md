```
arg_mkdir(f::Function, arg::AbstractString) -> arg
arg_mkdir(f::Function, arg::Nothing) -> mktempdir()
```

`arg_mkdir` 함수는 `arg`를 받아들이며, 이는 다음 중 하나여야 합니다:

  * 이미 존재하는 빈 디렉토리에 대한 경로,
  * 디렉토리로 생성할 수 있는 존재하지 않는 경로, 또는
  * `nothing`인 경우, 임시 디렉토리가 생성됩니다.

모든 경우에 디렉토리에 대한 경로가 반환됩니다. `f(arg)` 실행 중 오류가 발생하면, 디렉토리는 원래 상태로 복원됩니다: 이미 존재했지만 비어 있었다면 비워지고, 존재하지 않았다면 삭제됩니다.
