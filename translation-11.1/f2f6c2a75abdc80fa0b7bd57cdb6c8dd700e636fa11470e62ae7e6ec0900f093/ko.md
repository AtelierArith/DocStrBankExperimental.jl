```
callers(funcname, [data, lidict], [filename=<filename>], [linerange=<start:stop>]) -> Vector{Tuple{count, lineinfo}}
```

이전 프로파일링 실행을 기반으로 특정 함수를 호출한 사람을 확인합니다. 파일 이름(선택적으로 함수가 정의된 줄 번호 범위)을 제공하면 오버로드된 메서드를 구분할 수 있습니다. 반환 값은 호출 수와 호출자에 대한 줄 정보가 포함된 벡터입니다. 선택적으로 [`retrieve`](@ref)에서 얻은 백트레이스 `data`를 제공할 수 있으며, 그렇지 않으면 현재 내부 프로파일 버퍼가 사용됩니다.
