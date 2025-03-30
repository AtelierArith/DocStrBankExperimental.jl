```
print([io::IO = stdout,] data::Vector, lidict::LineInfoDict; kwargs...)
```

`io`에 프로파일링 결과를 출력합니다. 이 변형은 이전에 [`retrieve`](@ref) 호출로 내보낸 결과를 검사하는 데 사용됩니다. 백트레이스의 벡터 `data`와 줄 정보의 사전 `lidict`를 제공합니다.

유효한 키워드 인수에 대한 설명은 `Profile.print([io], data)`를 참조하십시오.
