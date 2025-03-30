```
llvmcall(fun_ir::String, returntype, Tuple{argtype1, ...}, argvalue1, ...)
llvmcall((mod_ir::String, entry_fn::String), returntype, Tuple{argtype1, ...}, argvalue1, ...)
llvmcall((mod_bc::Vector{UInt8}, entry_fn::String), returntype, Tuple{argtype1, ...}, argvalue1, ...)
```

첫 번째 인수로 제공된 LLVM 코드를 호출합니다. 이 첫 번째 인수를 지정하는 방법에는 여러 가지가 있습니다:

  * 함수 수준 IR을 나타내는 리터럴 문자열로, 인수는 연속적인 이름 없는 SSA 변수(%0, %1 등)로 사용 가능합니다;
  * 모듈 IR의 문자열과 호출할 진입점 함수의 이름을 나타내는 문자열을 포함하는 2요소 튜플로;
  * 비트코드로 제공된 모듈을 가진 `Vector{UInt8}`로, 하지만 2요소 튜플로.

`ccall`과는 달리, 인수 유형은 튜플 유형으로 지정해야 하며, 유형의 튜플이 아닙니다. 모든 유형과 LLVM 코드는 리터럴로 지정해야 하며, 변수나 표현식이 아니어야 합니다(이러한 리터럴을 생성하기 위해 `@eval`을 사용해야 할 수도 있습니다).

[불투명 포인터](https://llvm.org/docs/OpaquePointers.html) ( `ptr`로 작성됨)는 LLVM 코드에서 허용되지 않습니다.

사용 예는 [`test/llvmcall.jl`](https://github.com/JuliaLang/julia/blob/v1.11.4/test/llvmcall.jl)를 참조하세요.
