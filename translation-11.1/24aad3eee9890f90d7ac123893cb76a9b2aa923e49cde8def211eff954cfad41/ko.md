```
arg_isdir(f::Function, arg::AbstractString) -> f(arg)
```

`arg_isdir` 함수는 `arg`를 받아들이며, 이는 기존 디렉토리의 경로여야 합니다(그렇지 않으면 오류가 발생합니다) 그리고 그 경로를 `f`에 전달하여 최종적으로 `f(arg)`의 결과를 반환합니다. 이는 확실히 `ArgTools`에서 제공하는 가장 덜 유용한 도구이며, 주로 `arg_mkdir`와의 대칭성을 위해 존재하고 일관된 오류 메시지를 제공하기 위해 존재합니다.
