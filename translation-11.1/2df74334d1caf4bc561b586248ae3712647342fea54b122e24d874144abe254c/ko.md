```
cglobal((symbol, library) [, type=Cvoid])
```

C로 내보낸 공유 라이브러리에서 전역 변수에 대한 포인터를 가져옵니다. 이는 [`ccall`](@ref)에서 정확히 지정된 대로입니다. `Ptr{Type}`을 반환하며, `Type` 인수가 제공되지 않으면 기본적으로 `Ptr{Cvoid}`로 설정됩니다. 값은 각각 [`unsafe_load`](@ref) 또는 [`unsafe_store!`](@ref)를 통해 읽거나 쓸 수 있습니다.
