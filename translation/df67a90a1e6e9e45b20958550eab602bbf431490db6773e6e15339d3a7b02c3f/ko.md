```
redirect_stderr(f::Function, stream)
```

함수 `f`를 실행하면서 [`stderr`](@ref)를 `stream`으로 리디렉션합니다. 완료되면 [`stderr`](@ref)는 이전 설정으로 복원됩니다.
