```
Unicode.normalize(s::AbstractString; keywords...)
Unicode.normalize(s::AbstractString, normalform::Symbol)
```

문자열 `s`를 정규화합니다. 기본적으로, 정규화된 조합(`compose=true`)이 유니코드 버전 안정성을 보장하지 않고(`compat=false`) 수행되며, 이는 가능한 가장 짧은 동등 문자열을 생성하지만 이전 유니코드 버전에는 없는 조합 문자를 도입할 수 있습니다.

대신, 유니코드 표준의 네 가지 "정규형" 중 하나를 지정할 수 있습니다: `normalform`은 `:NFC`, `:NFD`, `:NFKC`, 또는 `:NFKD`일 수 있습니다. 정규형 C(정규 조합)와 D(정규 분해)는 동일한 추상 문자열의 서로 다른 시각적으로 동일한 표현을 단일 정규형으로 변환하며, C형이 더 간결합니다. 정규형 KC와 KD는 추가적으로 "호환성 동등물"을 정규화합니다: 이들은 추상적으로 유사하지만 시각적으로 구별되는 문자를 단일 정규 선택으로 변환합니다(예: 리가처를 개별 문자로 확장함), KC형이 더 간결합니다.

대신, `Unicode.normalize(s; keywords...)`를 호출하여 더 세밀한 제어와 추가 변환을 얻을 수 있으며, 이때 다음의 불리언 키워드 옵션 중 아무거나 지정할 수 있습니다(모두 기본값은 `false`이며 `compose`를 제외하고):

  * `compose=false`: 정규 조합을 수행하지 않음
  * `decompose=true`: 정규 조합 대신 정규 분해를 수행함(`compose=true`가 존재할 경우 무시됨)
  * `compat=true`: 호환성 동등물이 정규화됨
  * `casefold=true`: 유니코드 대소문자 접기를 수행함, 예: 대소문자 구분 없는 문자열 비교를 위해
  * `newline2lf=true`, `newline2ls=true`, 또는 `newline2ps=true`: 다양한 줄 바꿈 시퀀스(LF, CRLF, CR, NEL)를 각각 줄 바꿈(LF), 줄 구분(LS), 또는 단락 구분(PS) 문자로 변환함
  * `stripmark=true`: 발음 기호를 제거함(예: 악센트)
  * `stripignore=true`: 유니코드의 "기본 무시 가능" 문자를 제거함(예: 소프트 하이픈 또는 왼쪽에서 오른쪽으로의 마커)
  * `stripcc=true`: 제어 문자를 제거함; 수평 탭과 폼 피드는 공백으로 변환됨; 줄 바꿈도 줄 바꿈 변환 플래그가 지정되지 않는 한 공백으로 변환됨
  * `rejectna=true`: 할당되지 않은 코드 포인트가 발견되면 오류를 발생시킴
  * `stable=true`: 유니코드 버전 안정성을 강제함(이전 유니코드 버전에서 누락된 문자를 절대 도입하지 않음)

또한, `chartransform` 키워드(기본값은 `identity`)를 사용하여 `Integer` 코드 포인트를 코드 포인트로 매핑하는 임의의 *함수*를 전달할 수 있으며, 이는 `s`의 각 문자가 처리될 때 호출되어 임의의 추가 정규화를 수행합니다. 예를 들어, `chartransform=Unicode.julia_chartransform`을 전달하면, 식별자를 구문 분석할 때 줄리아가 수행하는 몇 가지 줄리아 특정 문자 정규화를 적용할 수 있습니다(또한 NFC 정규화: `compose=true, stable=true`).

예를 들어, NFKC는 옵션 `compose=true, compat=true, stable=true`에 해당합니다.

# 예시

```jldoctest
julia> "é" == Unicode.normalize("é") #LHS: Unicode U+00e9, RHS: U+0065 & U+0301
true

julia> "μ" == Unicode.normalize("µ", compat=true) #LHS: Unicode U+03bc, RHS: Unicode U+00b5
true

julia> Unicode.normalize("JuLiA", casefold=true)
"julia"

julia> Unicode.normalize("JúLiA", stripmark=true)
"JuLiA"
```

!!! compat "Julia 1.8"
    `chartransform` 키워드 인자는 Julia 1.8이 필요합니다.

