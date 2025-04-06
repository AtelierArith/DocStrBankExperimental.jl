```
마지막으로
```

주어진 코드 블록이 어떻게 종료되든지 간에 코드를 실행합니다. 예를 들어, 열린 파일이 닫히도록 보장하는 방법은 다음과 같습니다:

```julia
f = open("file")
try
    operate_on_file(f)
finally
    close(f)
end
```

제어가 [`try`](@ref) 블록을 떠날 때(예: [`return`](@ref)으로 인해, 또는 그냥 정상적으로 종료되는 경우) [`close(f)`](@ref)가 실행됩니다. `try` 블록이 예외로 인해 종료되면, 예외는 계속 전파됩니다. `catch` 블록은 `try` 및 `finally`와 결합될 수 있습니다. 이 경우 `finally` 블록은 `catch`가 오류를 처리한 후에 실행됩니다.
