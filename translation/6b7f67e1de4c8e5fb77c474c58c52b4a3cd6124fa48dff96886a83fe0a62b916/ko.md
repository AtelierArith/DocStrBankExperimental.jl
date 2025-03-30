```
TestCounts
```

테스트 세트의 결과를 재귀적으로 수집하여 표시하기 위한 상태를 보유합니다.

필드:

  * `customized`: `get_test_counts` 함수가 이 카운트 객체에 대한 `AbstractTestSet`에 맞게 사용자 정의되었는지 여부. 사용자 정의 메서드가 정의된 경우, 항상 생성자에 `true`를 전달하십시오.
  * `passes`: 통과한 `@test` 호출의 수.
  * `fails`: 실패한 `@test` 호출의 수.
  * `errors`: 오류가 발생한 `@test` 호출의 수.
  * `broken`: 고장난 `@test` 호출의 수.
  * `passes`: 통과한 `@test` 호출의 누적 수.
  * `fails`: 실패한 `@test` 호출의 누적 수.
  * `errors`: 오류가 발생한 `@test` 호출의 누적 수.
  * `broken`: 고장난 `@test` 호출의 누적 수.
  * `duration`: 해당 `AbstractTestSet`이 실행된 총 지속 시간, 형식화된 `String`으로.
