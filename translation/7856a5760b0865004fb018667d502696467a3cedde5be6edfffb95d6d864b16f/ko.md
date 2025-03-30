```
RoundingMode
```

부동 소수점 연산의 반올림 모드를 제어하는 데 사용되는 유형( [`rounding`](@ref)/[`setrounding`](@ref) 함수 사용) 또는 가장 가까운 정수로 반올림하기 위한 선택적 인수로 사용됩니다( [`round`](@ref) 함수 사용).

현재 지원되는 반올림 모드는 다음과 같습니다:

  * [`RoundNearest`](@ref) (기본값)
  * [`RoundNearestTiesAway`](@ref)
  * [`RoundNearestTiesUp`](@ref)
  * [`RoundToZero`](@ref)
  * [`RoundFromZero`](@ref)
  * [`RoundUp`](@ref)
  * [`RoundDown`](@ref)

!!! compat "Julia 1.9"
    `RoundFromZero`는 최소한 Julia 1.9가 필요합니다. 이전 버전은 `BigFloat`에 대해서만 `RoundFromZero`를 지원합니다.

