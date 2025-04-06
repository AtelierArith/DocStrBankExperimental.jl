```
GitShortHash(hash::GitHash, len::Integer)
```

고유할 때 git 객체를 식별하는 데 사용할 수 있는 축약된 git 객체 식별자로, `hash`의 처음 `len` 개 16진수 숫자로 구성되며 (나머지 숫자는 무시됨).
