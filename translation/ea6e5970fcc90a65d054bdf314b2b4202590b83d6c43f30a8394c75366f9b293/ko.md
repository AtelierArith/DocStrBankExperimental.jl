```
reenable_sigint(f::Function)
```

함수 실행 중 Ctrl-C 핸들러를 다시 활성화합니다. [`disable_sigint`](@ref)의 효과를 일시적으로 되돌립니다.
