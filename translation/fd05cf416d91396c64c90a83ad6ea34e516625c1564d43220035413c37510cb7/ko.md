```
list(tarball; [ strict = true ]) -> Vector{Header}
list(callback, tarball; [ strict = true ])

    callback  :: Header, [ <data> ] --> Any
    tarball   :: Union{AbstractString, AbstractCmd, IO}
    strict    :: Bool
```

주어진 경로 `tarball`에 위치한 tar 아카이브("tarball")의 내용을 나열합니다. `tarball`이 IO 핸들이면 해당 스트림에서 tar 내용을 읽습니다. `Header` 구조체의 벡터를 반환합니다. 자세한 내용은 [`Header`](@ref)를 참조하십시오.

`callback`이 제공되면 헤더의 벡터를 반환하는 대신 각 `Header`에 대해 콜백이 호출됩니다. 이는 tarball의 항목 수가 많거나 tarball의 오류 이전에 항목을 검사하고 싶을 때 유용할 수 있습니다. `callback` 함수가 `Vector{UInt8}` 또는 `Vector{Pair{Symbol, String}}` 유형의 두 번째 인수를 수용할 수 있는 경우, 원시 헤더 데이터의 표현으로 호출되며, 이는 단일 바이트 벡터 또는 필드 이름을 해당 필드의 원시 데이터에 매핑하는 쌍의 벡터로 제공됩니다(이 필드들이 함께 연결되면 결과는 헤더의 원시 데이터입니다).

기본적으로 `list`는 `extract` 함수가 추출을 거부할 tarball 내용이 발견되면 오류를 발생시킵니다. `strict=false`로 설정하면 이러한 검사를 건너뛰고 `extract`가 추출할 수 있는지 여부에 관계없이 tar 파일의 모든 내용을 나열합니다. 악의적인 tarball은 당신을 속이기 위해 여러 가지 교묘하고 예상치 못한 일을 할 수 있으니 주의하십시오.

`tarball` 인수가 스켈레톤 파일(see `extract` and `create`)인 경우, `list`는 파일 헤더에서 이를 감지하고 스켈레톤 파일의 헤더를 적절하게 나열하거나 반복합니다.
