```
devnull
```

스트림 리디렉션에서 사용되어 여기에 기록된 모든 데이터를 버립니다. 본질적으로 Unix의 `/dev/null` 또는 Windows의 `NUL`과 동등합니다. 사용법:

```julia
run(pipeline(`cat test.txt`, devnull))
```
