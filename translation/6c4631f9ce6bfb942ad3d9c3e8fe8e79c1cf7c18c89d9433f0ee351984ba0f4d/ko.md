```
pipeline(command; stdin, stdout, stderr, append=false)
```

주어진 `command`로부터 I/O를 리디렉션합니다. 키워드 인자는 어떤 명령의 스트림이 리디렉션되어야 하는지를 지정합니다. `append`는 파일 출력이 파일에 추가되는지를 제어합니다. 이는 2-인자 `pipeline` 함수의 더 일반적인 버전입니다. `pipeline(from, to)`는 `from`이 명령일 때 `pipeline(from, stdout=to)`와 동등하며, `from`이 다른 종류의 데이터 소스일 때는 `pipeline(to, stdin=from)`과 동등합니다.

**예제**:

```julia
run(pipeline(`dothings`, stdout="out.txt", stderr="errs.txt"))
run(pipeline(`update`, stdout="log.txt", append=true))
```
