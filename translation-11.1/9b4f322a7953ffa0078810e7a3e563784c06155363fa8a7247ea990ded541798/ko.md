# High-level Overview of the Native-Code Generation Process

## Representation of Pointers

코드가 객체 파일로 방출될 때, 포인터는 재배치로 방출됩니다. 역직렬화 코드는 이러한 상수 중 하나를 가리키는 객체가 재생성되고 올바른 런타임 포인터를 포함하도록 보장합니다.

그렇지 않으면, 그것들은 리터럴 상수로 출력됩니다.

이 객체 중 하나를 방출하려면 `literal_pointer_val`을 호출하세요. 이 함수는 Julia 값과 LLVM 글로벌을 추적하여 현재 런타임과 역직렬화 후에도 유효하도록 보장합니다.

객체 파일에 방출될 때, 이러한 전역 변수들은 큰 `gvals` 테이블에 참조로 저장됩니다. 이는 역직렬화기가 인덱스로 이들을 참조할 수 있게 하며, 전역 오프셋 테이블(GOT)과 유사한 사용자 정의 수동 메커니즘을 구현하여 이들을 복원할 수 있게 합니다.

함수 포인터는 유사하게 처리됩니다. 이들은 큰 `fvals` 테이블에 값으로 저장됩니다. 전역 변수와 마찬가지로, 이는 역직렬화기가 인덱스로 참조할 수 있게 해줍니다.

`extern` 함수는 일반적인 심볼 해석 메커니즘을 통해 링크에서 이름별로 별도로 처리된다는 점에 유의하세요.

`ccall` 함수는 수동 GOT 및 프로시저 링크 테이블(PLT)을 통해 별도로 처리된다는 점도 주목하세요.

## Representation of Intermediate Values

값은 `jl_cgval_t` 구조체로 전달됩니다. 이는 R-값을 나타내며, 이를 어디에 할당하거나 전달하는 방법을 결정하는 데 필요한 정보를 포함합니다.

그들은 일반적으로 `mark_julia_type` (즉각적인 값에 대해) 및 `mark_julia_slot` (값에 대한 포인터에 대해) 중 하나의 도우미 생성자를 통해 생성됩니다.

함수 `convert_julia_type`는 두 가지 유형 간의 변환을 수행할 수 있습니다. 이 함수는 `cgval.typ`이 `typ`으로 설정된 R-값을 반환합니다. 요청된 표현으로 객체를 변환하며, 필요에 따라 힙 박스를 만들고, 스택 복사본을 할당하며, 태그가 있는 유니온을 계산하여 표현을 변경합니다.

대조적으로 `update_julia_type`는 `cgval.typ`을 `typ`으로 변경하지만, 이는 제로 비용(즉, 어떤 코드도 생성하지 않고)으로 가능할 경우에만 수행됩니다.

## Union representation

추론된 유니온 타입은 태그가 있는 타입 표현을 통해 스택에 할당될 수 있습니다.

태그가 있는 유니온을 처리할 수 있어야 하는 기본 루틴은 다음과 같습니다:

  * 마크-타입
  * 로컬 로드
  * store-local
  * isa
  * is
  * emit_typeof
  * emit_sizeof
  * 상자에 담긴
  * 언박스
  * specialized cc-ret

모든 나머지는 이러한 원시 요소를 사용하여 유니온 분할을 구현함으로써 추론에서 처리할 수 있어야 합니다.

태그된 유니온의 표현은 `< void* union, byte selector >` 쌍으로 구성됩니다. 선택자는 `byte & 0x7f`로 고정 크기이며, 처음 126개의 isbits를 유니온 태그로 지정합니다. 이는 isbits 객체 내부의 타입 유니온에 대한 1 기반 깊이 우선 카운트를 기록합니다. 인덱스가 0이면 `union*`이 실제로 태그가 있는 힙 할당된 `jl_value_t*`임을 나타내며, 태그된 유니온이 아닌 박스된 객체로 정상적으로 처리해야 합니다.

선택자의 상위 비트(`byte & 0x80`)를 테스트하여 `void*`가 실제로 힙에 할당된(`jl_value_t*`) 박스인지 확인할 수 있습니다. 이렇게 하면 박스를 재할당하는 비용을 피하면서 낮은 비트를 기반으로 한 유니온 분할을 효율적으로 처리할 수 있는 능력을 유지할 수 있습니다.

`byte & 0x7f`는 값이 태그로 표현될 수 있는 경우에 대한 정확한 테스트를 보장합니다. 이 값은 절대 `byte = 0x80`으로 표시되지 않습니다. `isa`를 테스트할 때 타입 태그를 추가로 테스트할 필요는 없습니다.

`union*` 메모리 영역은 *어떤* 크기로도 할당될 수 있습니다. 유일한 제약 조건은 현재 `selector`에 의해 지정된 데이터를 포함할 수 있을 만큼 충분히 커야 한다는 것입니다. 관련된 Union 타입 필드에 따라 저장될 수 있는 모든 타입의 합을 포함하기에는 충분하지 않을 수 있습니다. 복사할 때 적절한 주의를 기울이십시오.

## Specialized Calling Convention Signature Representation

`jl_returninfo_t` 객체는 호출 가능한 모든 것의 호출 규약 세부정보를 설명합니다.

메서드의 인수나 반환 타입 중 어떤 것이 언박스된 형태로 표현될 수 있고, 메서드가 가변 인자가 아닐 경우, 해당 메서드는 `specTypes` 및 `rettype` 필드를 기반으로 최적화된 호출 규약 서명을 부여받게 됩니다.

일반적인 원칙은 다음과 같습니다:

  * 원시 타입은 int/float 레지스터에 전달됩니다.
  * VecElement 유형의 튜플은 벡터 레지스터에 전달됩니다.
  * 구조체는 스택에 전달됩니다.
  * 반환 값은 인수와 유사하게 처리되며, 숨겨진 sret 인수를 통해 반환되는 크기 컷오프가 있습니다.

이의 전체 논리는 `get_specsig_function`과 `deserves_sret`에 의해 구현됩니다.

또한, 반환 유형이 유니온인 경우, 값 쌍(포인터와 태그)으로 반환될 수 있습니다. 유니온 값이 스택에 할당될 수 있는 경우, 이를 저장할 충분한 공간도 숨겨진 첫 번째 인수로 전달됩니다. 반환된 포인터가 이 공간, 박스된 객체 또는 다른 상수 메모리를 가리킬지는 호출된 함수에 달려 있습니다.
