```
setrounding(f::Function, T, mode)
```

함수 `f`의 실행 동안 부동 소수점 타입 `T`의 반올림 모드를 변경합니다. 이는 논리적으로 다음과 같습니다:

```
old = rounding(T)
setrounding(T, mode)
f()
setrounding(T, old)
```

사용 가능한 반올림 모드는 [`RoundingMode`](@ref)를 참조하세요.
