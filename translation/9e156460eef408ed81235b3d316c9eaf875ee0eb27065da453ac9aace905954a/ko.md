```
@lock l expr
```

`lock(f, l::AbstractLock)`의 매크로 버전이지만 `f` 함수 대신 `expr`을 사용합니다. 다음과 같이 확장됩니다:

```julia
lock(l)
try
    expr
finally
    unlock(l)
end
```

이는 `do` 블록과 함께 [`lock`](@ref)를 사용하는 것과 유사하지만 클로저를 생성하지 않으므로 성능을 향상시킬 수 있습니다.

!!! compat
    `@lock`은 Julia 1.3에 추가되었으며, Julia 1.10에서 내보내졌습니다.

