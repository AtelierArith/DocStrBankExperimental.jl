```
redirect_stdout(f::Function, stream)
```

함수 `f`를 실행하면서 [`stdout`](@ref)를 `stream`으로 리디렉션합니다. 완료되면 [`stdout`](@ref)는 이전 설정으로 복원됩니다.
