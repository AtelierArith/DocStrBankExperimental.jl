A [`Face`](@ref)는 텍스트를 표시하기 위한 그래픽 속성의 모음입니다. Faces는 텍스트가 터미널 및 아마도 다른 장소에서 어떻게 표시되는지를 제어합니다.

대부분의 경우, [`Face`](@ref)는 고유한 *face name* 기호와의 연관으로 전역 faces dicts에 저장되며, [`Face`](@ref) 객체 자체보다 이 이름으로 더 자주 참조됩니다.

# 속성

모든 속성은 키워드 생성자를 통해 설정할 수 있으며 기본값은 `nothing`입니다.

  * `height` (an `Int` or `Float64`): 높이는 deci-pt(정수일 때) 또는 기본 크기의 배수(실수일 때)로 설정됩니다.
  * `weight` (a `Symbol`): 가장 연한 것부터 가장 진한 것까지의 기호 중 하나인 `:thin`, `:extralight`, `:light`, `:semilight`, `:normal`, `:medium`, `:semibold`, `:bold`, `:extrabold`, 또는 `:black`. 터미널에서는 `:normal`보다 큰 모든 무게가 굵게 표시되며, 가변 밝기 텍스트를 지원하는 터미널에서는 `:normal`보다 작은 모든 무게가 연하게 표시됩니다.
  * `slant` (a `Symbol`): 기호 중 하나인 `:italic`, `:oblique`, 또는 `:normal`.
  * `foreground` (a `SimpleColor`): 텍스트 전경 색상.
  * `background` (a `SimpleColor`): 텍스트 배경 색상.
  * `underline`, 텍스트 밑줄로, 다음 형태 중 하나를 취합니다:

      * a `Bool`: 텍스트에 밑줄을 긋는지 여부.
      * a `SimpleColor`: 이 색상으로 텍스트에 밑줄을 긋습니다.
      * a `Tuple{Nothing, Symbol}`: 기호에 의해 설정된 스타일로 텍스트에 밑줄을 긋습니다. 스타일은 `:straight`, `:double`, `:curly`, `:dotted`, 또는 `:dashed` 중 하나입니다.
      * a `Tuple{SimpleColor, Symbol}`: 지정된 SimpleColor로 텍스트에 밑줄을 긋고, 이전과 같이 기호에 의해 지정된 스타일을 사용합니다.
  * `strikethrough` (a `Bool`): 텍스트에 취소선을 긋는지 여부.
  * `inverse` (a `Bool`): 전경색과 배경색을 반전시킬지 여부.
  * `inherit` (a `Vector{Symbol}`): 상속할 face의 이름으로, 이전 face가 우선합니다. 모든 face는 `:default` face에서 상속됩니다.
