```
x::EscapeInfo
```

탈출 정보에 대한 격자로, 다음 속성을 포함합니다:

  * `x.Analyzed::Bool`: 격자의 공식적인 부분은 아니며, `x`가 분석되었는지를 나타냅니다.
  * `x.ReturnEscape::Bool`: `x`가 반환을 통해 호출자에게 탈출할 수 있음을 나타냅니다.
  * `x.ThrownEscape::BitSet`: `x`가 예외로 던져질 수 있는 SSA 문장 번호를 기록합니다:

      * `isempty(x.ThrownEscape)`: `x`는 이 호출 프레임에서 절대 던져지지 않습니다 (하단).
      * `pc ∈ x.ThrownEscape`: `x`는 `pc`의 SSA 문장에서 던져질 수 있습니다.
      * `-1 ∈ x.ThrownEscape`: `x`는 이 호출 프레임의 임의의 지점에서 던져질 수 있습니다 (상단).

    이 정보는 `escape_exception!`에 의해 예외를 통한 잠재적 탈출을 전파하는 데 사용됩니다.
  * `x.AliasInfo::Union{Bool,IndexableFields,IndexableElements,Unindexable}`: `x`의 필드 또는 배열 요소에 별칭을 가질 수 있는 모든 가능한 값을 유지합니다:

      * `x.AliasInfo === false`는 `x`의 필드/요소가 아직 분석되지 않았음을 나타냅니다.
      * `x.AliasInfo === true`는 `x`의 필드/요소가 분석될 수 없음을 나타냅니다. 예를 들어, `x`의 타입이 알려져 있지 않거나 구체적이지 않아서 그 필드/요소를 정확히 알 수 없습니다.
      * `x.AliasInfo::IndexableFields`는 객체 `x`의 필드에 별칭을 가질 수 있는 모든 가능한 값을 정확한 인덱스 정보와 함께 기록합니다.
      * `x.AliasInfo::IndexableElements`는 배열 `x`의 요소에 별칭을 가질 수 있는 모든 가능한 값을 정확한 인덱스 정보와 함께 기록합니다.
      * `x.AliasInfo::Unindexable`는 정확한 인덱스 정보 없이 `x`의 필드/요소에 별칭을 가질 수 있는 모든 가능한 값을 기록합니다.
  * `x.Liveness::BitSet`: `x`가 살아 있어야 하는 SSA 문장 번호를 기록합니다. 예를 들어, 호출 인수로 사용되거나 호출자에게 반환되거나 `:foreigncall`을 위해 보존되어야 합니다:

      * `isempty(x.Liveness)`: `x`는 이 호출 프레임에서 절대 사용되지 않습니다 (하단).
      * `0 ∈ x.Liveness`는 현재 분석 중인 호출 프레임의 호출 인수라는 특별한 의미를 가집니다 (따라서 호출자에게 즉시 보입니다).
      * `pc ∈ x.Liveness`: `x`는 `pc`의 SSA 문장에서 사용될 수 있습니다.
      * `-1 ∈ x.Liveness`: `x`는 이 호출 프레임의 임의의 지점에서 사용될 수 있습니다 (상단).

일반적인 `EscapeInfo`를 생성하기 위한 유틸리티 생성자가 있습니다. 예를 들어,

  * `NoEscape()`: 이 격자의 하단(-유사) 요소로, 어디에도 탈출하지 않음을 의미합니다.
  * `AllEscape()`: 이 격자의 최상위 요소로, 어디에나 탈출할 것임을 의미합니다.

`analyze_escapes`는 이러한 요소들을 하단에서 상단으로 전환하며, 이는 Julia의 기본 타입 추론 루틴과 같은 방향입니다. 추상 상태는 하단(-유사) 요소로 초기화됩니다:

  * 호출 인수는 `ArgEscape()`로 초기화되며, 그 `Liveness` 속성에는 `0`이 포함되어 호출 인수로 전달되고 호출자에게 즉시 보임을 나타냅니다.
  * 다른 상태는 `NotAnalyzed()`로 초기화되며, 이는 `NoEscape`보다 약간 낮은 특별한 격자 요소이지만, 동시에 아직 분석되지 않았다는 의미 외에는 어떤 의미도 나타내지 않습니다 (따라서 공식적으로 격자의 일부가 아닙니다).
