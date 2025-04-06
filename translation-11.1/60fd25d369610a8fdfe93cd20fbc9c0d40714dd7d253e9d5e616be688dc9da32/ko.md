```
@cfunction(callable, ReturnType, (ArgumentTypes...,)) -> Ptr{Cvoid}
@cfunction($callable, ReturnType, (ArgumentTypes...,)) -> CFunction
```

주어진 타입 서명에 대해 Julia 함수 `callable`에서 C 호출 가능 함수 포인터를 생성합니다. 반환 값을 `ccall`에 전달하려면 서명에서 인수 타입 `Ptr{Cvoid}`를 사용하십시오.

인수 타입 튜플은 리터럴 튜플이어야 하며, 튜플 값 변수나 표현식이 아니어야 합니다(스플랫 표현식을 포함할 수는 있지만). 이러한 인수는 컴파일 타임 동안 전역 범위에서 평가됩니다(런타임까지 연기되지 않음). 함수 인수 앞에 '$'를 추가하면 대신 로컬 변수 `callable`에 대한 런타임 클로저를 생성합니다(모든 아키텍처에서 지원되지 않습니다).

[ccall 및 cfunction 사용에 대한 매뉴얼 섹션](@ref Calling-C-and-Fortran-Code)을 참조하십시오.

# 예제

```julia-repl
julia> function foo(x::Int, y::Int)
           return x + y
       end

julia> @cfunction(foo, Int, (Int, Int))
Ptr{Cvoid} @0x000000001b82fcd0
```
