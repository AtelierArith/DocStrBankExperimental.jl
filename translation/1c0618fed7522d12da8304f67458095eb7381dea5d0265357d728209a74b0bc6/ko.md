```
pick(m::AbstractMenu, cursor::Int)
```

사용자가 메뉴가 열려 있는 동안 Enter 키를 누를 때 발생하는 일을 정의합니다. `true`가 반환되면 `request()`가 종료됩니다. `cursor`는 선택의 위치를 인덱싱합니다.
