```
run(command, args...; wait::Bool = true)
```

백틱으로 구성된 명령 객체를 실행합니다(매뉴얼의 [외부 프로그램 실행하기](@ref) 섹션을 참조). `wait`가 true일 때 프로세스가 비정상적으로 종료되거나 다른 문제가 발생하면 오류를 발생시킵니다.

`args...`를 사용하면 명령에 파일 설명자를 전달할 수 있으며, 일반 유닉스 파일 설명자와 같은 순서로 정렬됩니다(예: `stdin, stdout, stderr, FD(3), FD(4)...`).

`wait`가 false인 경우 프로세스는 비동기적으로 실행됩니다. 나중에 반환된 프로세스 객체에서 `success`를 호출하여 프로세스를 기다리고 종료 상태를 확인할 수 있습니다.

`wait`가 false인 경우 프로세스의 I/O 스트림은 `devnull`로 향합니다. `wait`가 true인 경우 I/O 스트림은 부모 프로세스와 공유됩니다. I/O 리디렉션을 제어하려면 [`pipeline`](@ref)를 사용하세요.
