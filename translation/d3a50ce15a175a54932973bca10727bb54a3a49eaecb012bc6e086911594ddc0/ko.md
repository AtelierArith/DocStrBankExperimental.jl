```
ArgWrite = Union{AbstractString, AbstractCmd, IO}
```

`ArgWrite` 타입은 `arg_write` 함수가 쓰기 가능한 IO 핸들로 변환하는 방법을 아는 타입들의 유니온이며, `Nothing`은 `arg_write`가 임시 파일을 생성하여 처리합니다. 자세한 내용은 [`arg_write`](@ref)를 참조하세요.
