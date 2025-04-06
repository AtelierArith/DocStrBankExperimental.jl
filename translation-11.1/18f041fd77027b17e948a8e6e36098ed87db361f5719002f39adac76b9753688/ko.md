```
LibGit2.reftype(ref::GitReference) -> Cint
```

`ref`의 유형에 해당하는 `Cint`를 반환합니다:

  * 참조가 유효하지 않으면 `0`
  * 참조가 객체 ID이면 `1`
  * 참조가 상징적이면 `2`
