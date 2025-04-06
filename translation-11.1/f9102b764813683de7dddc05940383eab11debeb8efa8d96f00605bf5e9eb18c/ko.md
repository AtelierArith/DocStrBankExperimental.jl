```
tempdir()
```

임시 디렉토리의 경로를 가져옵니다. Windows에서는 `tempdir()`이 정렬된 목록 `TMP`, `TEMP`, `USERPROFILE`에서 발견된 첫 번째 환경 변수를 사용합니다. 다른 모든 운영 체제에서는 `tempdir()`이 정렬된 목록 `TMPDIR`, `TMP`, `TEMP`, `TEMPDIR`에서 발견된 첫 번째 환경 변수를 사용합니다. 이러한 변수 중 어느 것도 발견되지 않으면 경로 `"/tmp"`가 사용됩니다.
