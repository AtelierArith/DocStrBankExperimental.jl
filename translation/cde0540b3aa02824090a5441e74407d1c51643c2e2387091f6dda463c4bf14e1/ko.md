```
remove_frames!(stack::StackTrace, name::Symbol)
```

`StackTrace`(즉, `StackFrames`의 벡터)와 함수 이름(즉, `Symbol`)을 받아서, 함수 이름으로 지정된 `StackFrame`을 `StackTrace`에서 제거하고(지정된 함수 위의 모든 프레임도 제거함), 주로 반환하기 전에 `StackTrace`에서 함수의 `StackTraces`를 제거하는 데 사용됩니다.
