# Calling Conventions

줄리아는 네 가지 뚜렷한 목적을 위해 세 가지 호출 규약을 사용합니다:

| Name    | Prefix    | Purpose                          |
|:------- |:--------- |:-------------------------------- |
| Native  | `julia_`  | Speed via specialized signatures |
| JL Call | `jlcall_` | Wrapper for generic calls        |
| JL Call | `jl_`     | Builtins                         |
| C ABI   | `jlcapi_` | Wrapper callable from C          |

## Julia Native Calling Convention

네이티브 호출 규약은 빠른 비제네릭 호출을 위해 설계되었습니다. 일반적으로 특수화된 서명을 사용합니다.

  * LLVM 유령(제로 길이 타입)은 생략됩니다.
  * LLVM 스칼라와 벡터는 값에 의해 전달됩니다.
  * LLVM 집합체(배열 및 구조체)는 참조로 전달됩니다.

작은 반환 값은 LLVM 반환 값으로 반환됩니다. 큰 반환 값은 "구조체 반환"(`sret`) 규칙을 통해 반환되며, 호출자가 반환 슬롯에 대한 포인터를 제공합니다.

동일한 요소로 구성된 튜플인 인수 또는 반환 값은 때때로 LLVM 배열 대신 LLVM 벡터로 표현됩니다.

## JL Call Convention

JL 호출 규약은 내장 함수 및 일반 디스패치를 위한 것입니다. 이 규약을 사용하는 수동 작성 함수는 매크로 `JL_CALLABLE`을 통해 선언됩니다. 이 규약은 정확히 3개의 매개변수를 사용합니다:

  * `F`  - 적용되고 있는 함수의 줄리아 표현
  * `args` - 상자에 대한 포인터 배열의 포인터
  * `nargs` - 배열의 길이

반환 값은 상자를 가리키는 포인터입니다.

## C ABI

C ABI 래퍼는 C에서 Julia를 호출할 수 있게 해줍니다. 래퍼는 네이티브 호출 규약을 사용하여 함수를 호출합니다.

튜플은 항상 C 배열로 표현됩니다.
