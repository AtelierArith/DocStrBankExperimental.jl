```
PipeBuffer(data::AbstractVector{UInt8}=UInt8[]; maxsize::Integer = typemax(Int))
```

읽기를 허용하고 추가하여 쓰기를 수행하는 [`IOBuffer`](@ref)입니다. 탐색 및 잘라내기는 지원되지 않습니다. 사용 가능한 생성자에 대해서는 [`IOBuffer`](@ref)를 참조하십시오. `data`가 주어지면 데이터 벡터에서 작동하는 `PipeBuffer`를 생성하며, 선택적으로 기본 `Array`가 성장할 수 없는 크기를 지정합니다.
