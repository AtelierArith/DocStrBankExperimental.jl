```
dlclose(::Nothing)
```

매우 일반적인 사용 패턴인

```
try
    hdl = dlopen(library_name)
    ... do something
finally
    dlclose(hdl)
end
```

에 대해, `library_name`이 발견되지 않은 경우 사용자 코드가 동작을 변경할 필요가 없도록 `Nothing` 타입의 매개변수를 받는 `dlclose()` 메서드를 정의합니다.
