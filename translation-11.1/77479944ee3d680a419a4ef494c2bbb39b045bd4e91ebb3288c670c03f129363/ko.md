```
pushdisplay(d::AbstractDisplay)
```

전역 디스플레이 백엔드 스택의 맨 위에 새로운 디스플레이 `d`를 푸시합니다. `display(x)` 또는 `display(mime, x)`를 호출하면 스택에서 호환 가능한 맨 위의 백엔드(즉, [`MethodError`](@ref)를 발생시키지 않는 맨 위의 백엔드)에서 `x`가 표시됩니다.
