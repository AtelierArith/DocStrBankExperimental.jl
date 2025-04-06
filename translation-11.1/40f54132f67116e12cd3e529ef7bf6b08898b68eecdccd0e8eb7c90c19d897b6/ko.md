```
print([io::IO = stdout,] [data::Vector = fetch()], [lidict::Union{LineInfoDict, LineInfoFlatDict} = getdict(data)]; kwargs...)
```

`io`에 프로파일링 결과를 출력합니다(기본값은 `stdout`). `data` 벡터를 제공하지 않으면, 누적된 백트레이스의 내부 버퍼가 사용됩니다.

키워드 인수는 다음의 조합이 가능합니다:

  * `format` – 백트레이스가 트리 구조를 나타내는 들여쓰기와 함께(`:tree`, 기본값) 또는 없이(`:flat`) 출력되는지를 결정합니다.
  * `C` – `true`인 경우, C 및 Fortran 코드의 백트레이스가 표시됩니다(정상적으로는 제외됨).
  * `combine` – `true`인 경우(기본값), 동일한 코드 줄에 해당하는 명령 포인터가 병합됩니다.
  * `maxdepth` – `:tree` 형식에서 `maxdepth`보다 깊이를 제한합니다.
  * `sortedby` – `:flat` 형식에서의 순서를 제어합니다. `:filefuncline`(기본값)은 소스 줄에 따라 정렬하고, `:count`는 수집된 샘플 수에 따라 정렬하며, `:overhead`는 각 함수가 자체적으로 발생시킨 샘플 수에 따라 정렬합니다.
  * `groupby` – 작업 및 스레드에 대한 그룹화를 제어하거나 그룹화를 하지 않습니다. 옵션은 `:none`(기본값), `:thread`, `:task`, `[:thread, :task]`, 또는 `[:task, :thread]`로, 마지막 두 가지는 중첩 그룹화를 제공합니다.
  * `noisefloor` – 샘플의 휴리스틱 노이즈 바닥을 초과하는 프레임을 제한합니다(형식 `:tree`에만 적용됨). 이를 위해 시도해볼 제안 값은 2.0입니다(기본값은 0). 이 매개변수는 `n <= noisefloor * √N`인 샘플을 숨깁니다. 여기서 `n`은 이 줄의 샘플 수이고, `N`은 호출자의 샘플 수입니다.
  * `mincount` – 최소 `mincount` 발생이 있는 줄만 출력으로 제한합니다.
  * `recur` – `:tree` 형식에서 재귀 처리를 제어합니다. `:off`(기본값)는 트리를 정상적으로 출력합니다. `:flat`은 대신 재귀를 압축하여(아이피 기준) 자기 재귀를 반복자로 변환하는 대략적인 효과를 보여줍니다. `:flatc`는 동일하지만 C 프레임의 축소도 포함합니다(주변에서 `jl_apply`에 대해 이상한 동작을 할 수 있음).
  * `threads::Union{Int,AbstractVector{Int}}` – 보고서에 포함할 스레드를 지정합니다. 이는 샘플이 수집되는 스레드를 제어하지 않으며(다른 머신에서 수집되었을 수도 있음) 주의해야 합니다.
  * `tasks::Union{Int,AbstractVector{Int}}` – 보고서에 포함할 작업을 지정합니다. 이는 샘플이 수집되는 작업을 제어하지 않습니다.

!!! compat "Julia 1.8"
    `groupby`, `threads`, 및 `tasks` 키워드 인수는 Julia 1.8에서 도입되었습니다.


!!! note
    Windows에서의 프로파일링은 메인 스레드로 제한됩니다. 다른 스레드는 샘플링되지 않았으며 보고서에 표시되지 않습니다.

