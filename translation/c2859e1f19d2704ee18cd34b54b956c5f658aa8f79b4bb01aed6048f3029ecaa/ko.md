```
finalizer(f, x)
```

함수 `f(x)`를 등록하여 `x`에 대한 프로그램 접근 가능한 참조가 없을 때 호출되도록 하고, `x`를 반환합니다. `x`의 타입은 `mutable struct`이어야 하며, 그렇지 않으면 함수가 예외를 발생시킵니다.

`f`는 작업 전환을 유발해서는 안 되며, 이는 `println`과 같은 대부분의 I/O 작업을 제외합니다. 디버깅 목적으로 `@async` 매크로(파이널라이저 외부에서 컨텍스트 전환을 연기하기 위해 사용) 또는 C에서 I/O 함수를 직접 호출하기 위한 `ccall`을 사용하는 것이 도움이 될 수 있습니다.

`f`의 실행에 대한 보장된 세계 나이는 없다는 점에 유의하십시오. `f`는 파이널라이저가 등록된 세계 나이 또는 이후의 어떤 세계 나이에서 호출될 수 있습니다.

# 예제

```julia
finalizer(my_mutable_struct) do x
    @async println("Finalizing $x.")
end

finalizer(my_mutable_struct) do x
    ccall(:jl_safe_printf, Cvoid, (Cstring, Cstring), "Finalizing %s.", repr(x))
end
```

파이널라이저는 객체 생성 시 등록될 수 있습니다. 다음 예제에서는 파이널라이저가 새로 생성된 가변 구조체 `x`를 반환하는 것에 암묵적으로 의존하고 있음을 주목하십시오.

```julia
mutable struct MyMutableStruct
    bar
    function MyMutableStruct(bar)
        x = new(bar)
        f(t) = @async println("Finalizing $t.")
        finalizer(f, x)
    end
end
```
