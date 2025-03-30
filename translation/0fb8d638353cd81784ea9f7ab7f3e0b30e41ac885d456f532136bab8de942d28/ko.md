```
@test_deprecated [pattern] expression
```

`--depwarn=yes`일 때, `expression`이 사용 중단 경고를 발생시키는지 테스트하고 `expression`의 값을 반환합니다. 로그 메시지 문자열은 기본적으로 `r"deprecated"i`에 대해 일치합니다.

`--depwarn=no`일 때, 단순히 `expression`을 실행한 결과를 반환합니다. `--depwarn=error`일 때, `ErrorException`이 발생하는지 확인합니다.

# 예제

```
# julia 0.7에서 사용 중단됨
@test_deprecated num2hex(1)

# 반환된 값은 @test와 연결하여 테스트할 수 있습니다:
@test (@test_deprecated num2hex(1)) == "0000000000000001"
```
