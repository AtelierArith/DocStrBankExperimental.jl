```
try/catch
```

`try`/`catch` 문은 [`throw`](@ref)로 발생한 오류(예외)를 가로채어 프로그램 실행을 계속할 수 있도록 합니다. 예를 들어, 다음 코드는 파일을 쓰려고 시도하지만, 파일을 쓸 수 없는 경우 사용자에게 경고하고 실행을 종료하는 대신 계속 진행합니다:

```julia
try
    open("/danger", "w") do f
        println(f, "Hello")
    end
catch
    @warn "Could not write file."
end
```

또는, 파일을 변수에 읽을 수 없는 경우:

```julia
lines = try
    open("/danger", "r") do f
        readlines(f)
    end
catch
    @warn "File not found."
end
```

`catch e` 구문(여기서 `e`는 임의의 변수)은 `catch` 블록 내에서 발생한 예외 객체를 주어진 변수에 할당합니다.

`try`/`catch` 구조의 힘은 깊게 중첩된 계산을 즉시 호출 함수 스택의 훨씬 높은 수준으로 풀어낼 수 있는 능력에 있습니다.
