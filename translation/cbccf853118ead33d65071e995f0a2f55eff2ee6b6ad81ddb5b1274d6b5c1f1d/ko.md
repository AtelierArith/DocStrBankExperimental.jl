```
pipeline(from, to, ...)
```

데이터 소스에서 목적지로 파이프라인을 생성합니다. 소스와 목적지는 명령, I/O 스트림, 문자열 또는 다른 `pipeline` 호출의 결과일 수 있습니다. 최소한 하나의 인자는 명령이어야 합니다. 문자열은 파일 이름을 나타냅니다. 두 개 이상의 인자로 호출될 때, 왼쪽에서 오른쪽으로 연결됩니다. 예를 들어, `pipeline(a,b,c)`는 `pipeline(pipeline(a,b),c)`와 동일합니다. 이는 다단계 파이프라인을 지정하는 더 간결한 방법을 제공합니다.

**예제**:

```julia
run(pipeline(`ls`, `grep xyz`))
run(pipeline(`ls`, "out.txt"))
run(pipeline("out.txt", `grep xyz`))
```
