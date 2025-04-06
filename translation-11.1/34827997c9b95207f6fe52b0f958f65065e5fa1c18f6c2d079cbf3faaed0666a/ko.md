```
code_lowered(f, types; generated=true, debuginfo=:default)
```

주어진 일반 함수와 타입 서명에 맞는 메서드의 낮춰진 형태(IR)의 배열을 반환합니다.

`generated`가 `false`인 경우, 반환된 `CodeInfo` 인스턴스는 폴백 구현에 해당합니다. 폴백 구현이 존재하지 않으면 오류가 발생합니다. `generated`가 `true`인 경우, 이러한 `CodeInfo` 인스턴스는 생성기를 확장하여 생성된 메서드 본체에 해당합니다.

키워드 `debuginfo`는 출력에 존재하는 코드 메타데이터의 양을 제어합니다.

`generated`가 `true`이고 해당 메서드 중 하나가 `@generated` 메서드인 경우, `types`가 리프 타입이 아닐 때 오류가 발생합니다.
