# Calling C and Fortran Code

대부분의 코드는 Julia로 작성할 수 있지만, 이미 C와 Fortran으로 작성된 고품질의 성숙한 수치 계산 라이브러리가 많이 있습니다. 이러한 기존 코드를 쉽게 사용할 수 있도록 Julia는 C와 Fortran 함수를 호출하는 것을 간단하고 효율적으로 만듭니다. Julia는 "보일러플레이트 없음" 철학을 가지고 있습니다: 함수는 "접착" 코드, 코드 생성 또는 컴파일 없이 Julia에서 직접 호출할 수 있습니다 - 심지어 대화형 프롬프트에서도 가능합니다. 이는 적절한 호출을 [`@ccall`](@ref) 매크로(또는 덜 편리한 [`ccall`](@ref) 구문)를 사용하여 수행됩니다. 자세한 내용은 [`ccall` syntax section](@ref ccall-interface)를 참조하십시오.

코드가 호출되려면 공유 라이브러리로 제공되어야 합니다. 대부분의 C 및 Fortran 라이브러리는 이미 공유 라이브러리로 컴파일되어 제공되지만, GCC(또는 Clang)를 사용하여 코드를 직접 컴파일하는 경우 `-shared` 및 `-fPIC` 옵션을 사용해야 합니다. Julia의 JIT에 의해 생성된 기계 명령어는 네이티브 C 호출과 동일하므로, 결과적인 오버헤드는 C 코드에서 라이브러리 함수를 호출하는 것과 동일합니다. [^1]

기본적으로, Fortran 컴파일러는 [generate mangled names](https://en.wikipedia.org/wiki/Name_mangling#Fortran) (예: 함수 이름을 소문자 또는 대문자로 변환하고, 종종 언더스코어를 추가함)로 이름을 맹글링합니다. 따라서 Fortran 함수를 호출하려면 사용 중인 Fortran 컴파일러가 따르는 규칙에 해당하는 맹글링된 식별자를 전달해야 합니다. 또한, Fortran 함수를 호출할 때 모든 입력은 힙 또는 스택에 할당된 값에 대한 포인터로 전달되어야 합니다. 이는 일반적으로 힙에 할당되는 배열 및 기타 가변 객체뿐만 아니라, 일반적으로 스택에 할당되고 C 또는 Julia 호출 규약을 사용할 때 레지스터에 전달되는 정수 및 부동 소수점과 같은 스칼라 값에도 적용됩니다.

[`@ccall`](@ref)를 사용하여 라이브러리 함수 호출을 생성하는 구문은 다음과 같습니다:

```julia
  @ccall library.function_name(argvalue1::argtype1, ...)::returntype
  @ccall function_name(argvalue1::argtype1, ...)::returntype
  @ccall $function_pointer(argvalue1::argtype1, ...)::returntype
```

여기서 `library`는 문자열 상수 또는 리터럴입니다(하지만 아래의 [Non-constant Function Specifications](@ref)를 참조하십시오). 라이브러리는 생략할 수 있으며, 이 경우 함수 이름은 현재 프로세스에서 해결됩니다. 이 형식은 C 라이브러리 함수, Julia 런타임의 함수 또는 Julia에 연결된 애플리케이션의 함수를 호출하는 데 사용할 수 있습니다. 라이브러리에 대한 전체 경로도 지정할 수 있습니다. 또는 `@ccall`을 사용하여 `Libdl.dlsym`에 의해 반환된 것과 같은 함수 포인터 `$function_pointer`를 호출할 수도 있습니다. `argtype`는 C 함수 시그니처에 해당하고 `argvalue`는 함수에 전달될 실제 인수 값입니다.

!!! note
    아래를 참조하여 [map C types to Julia types](@ref mapping-c-types-to-julia)하는 방법을 확인하세요.


완전하지만 간단한 예로, 다음은 대부분의 유닉스 계열 시스템에서 표준 C 라이브러리의 `clock` 함수를 호출합니다:

```julia-repl
julia> t = @ccall clock()::Int32
2292761

julia> typeof(t)
Int32
```

`clock`는 인수를 받지 않으며 `Int32`를 반환합니다. 환경 변수의 값에 대한 포인터를 얻기 위해 `getenv` 함수를 호출하려면 다음과 같이 호출합니다:

```julia-repl
julia> path = @ccall getenv("SHELL"::Cstring)::Cstring
Cstring(@0x00007fff5fbffc45)

julia> unsafe_string(path)
"/bin/bash"
```

실제로, 특히 재사용 가능한 기능을 제공할 때, 일반적으로 `@ccall` 사용을 인수 설정 및 C 또는 Fortran 함수가 지정하는 방식으로 오류를 확인하는 Julia 함수로 래핑합니다. 오류가 발생하면 일반 Julia 예외로 발생합니다. 이는 C 및 Fortran API가 오류 조건을 나타내는 방식에 대해 일관성이 없기 때문에 특히 중요합니다. 예를 들어, `getenv` C 라이브러리 함수는 다음과 같은 Julia 함수로 래핑되며, 이는 [`env.jl`](https://github.com/JuliaLang/julia/blob/master/base/env.jl)의 실제 정의의 단순화된 버전입니다:

```julia
function getenv(var::AbstractString)
    val = @ccall getenv(var::Cstring)::Cstring
    if val == C_NULL
        error("getenv: undefined variable: ", var)
    end
    return unsafe_string(val)
end
```

C `getenv` 함수는 `C_NULL`을 반환하여 오류를 나타내지만, 다른 표준 C 함수들은 -1, 0, 1 및 기타 특별한 값을 반환하는 등 다른 방식으로 오류를 나타냅니다. 이 래퍼는 호출자가 존재하지 않는 환경 변수를 가져오려고 할 경우 문제를 나타내는 예외를 발생시킵니다:

```julia-repl
julia> getenv("SHELL")
"/bin/bash"

julia> getenv("FOOBAR")
ERROR: getenv: undefined variable: FOOBAR
```

여기 로컬 머신의 호스트 이름을 발견하는 약간 더 복잡한 예제가 있습니다.

```julia
function gethostname()
    hostname = Vector{UInt8}(undef, 256) # MAXHOSTNAMELEN
    err = @ccall gethostname(hostname::Ptr{UInt8}, sizeof(hostname)::Csize_t)::Int32
    Base.systemerror("gethostname", err != 0)
    hostname[end] = 0 # ensure null-termination
    return GC.@preserve hostname unsafe_string(pointer(hostname))
end
```

이 예제는 먼저 바이트 배열을 할당합니다. 그런 다음 C 라이브러리 함수 `gethostname`을 호출하여 배열을 호스트 이름으로 채웁니다. 마지막으로 호스트 이름 버퍼에 대한 포인터를 가져오고, 이를 널 종료 C 문자열로 가정하여 Julia 문자열로 변환합니다.

C 라이브러리에서 호출자가 호출자에게 전달할 메모리를 할당하고 이를 채우도록 요구하는 패턴은 일반적입니다. Julia에서 이렇게 메모리를 할당하는 것은 일반적으로 초기화되지 않은 배열을 생성하고 그 데이터에 대한 포인터를 C 함수에 전달함으로써 이루어집니다. 이것이 우리가 여기서 `Cstring` 유형을 사용하지 않는 이유입니다: 배열이 초기화되지 않았기 때문에 null 바이트를 포함할 수 있습니다. `@ccall`의 일환으로 `Cstring`으로 변환하면 포함된 null 바이트를 검사하므로 변환 오류가 발생할 수 있습니다.

`pointer(hostname)`를 `unsafe_string`으로 역참조하는 것은 안전하지 않은 작업입니다. 이는 `hostname`에 할당된 메모리에 접근해야 하는데, 이 메모리는 그 사이에 가비지 컬렉션에 의해 수거되었을 수 있습니다. 매크로 [`GC.@preserve`](@ref)는 이러한 일이 발생하는 것을 방지하며, 따라서 유효하지 않은 메모리 위치에 접근하는 것을 막습니다.

마지막으로, 경로를 통해 라이브러리를 지정하는 예가 있습니다. 다음 내용을 포함하여 공유 라이브러리를 생성합니다.

```c
#include <stdio.h>

void say_y(int y)
{
    printf("Hello from C: got y = %d.\n", y);
}
```

`gcc -fPIC -shared -o mylib.so mylib.c`로 컴파일합니다. 그런 다음 라이브러리 이름으로 (절대) 경로를 지정하여 호출할 수 있습니다:

```julia-repl
julia> @ccall "./mylib.so".say_y(5::Cint)::Cvoid
Hello from C: got y = 5.
```

## Creating C-Compatible Julia Function Pointers

Julia 함수를 함수 포인터 인수를 받는 네이티브 C 함수에 전달하는 것이 가능합니다. 예를 들어, 다음과 같은 C 프로토타입과 일치하도록:

```c
typedef returntype (*functiontype)(argumenttype, ...)
```

매크로 [`@cfunction`](@ref)는 줄리아 함수에 대한 C 호환 함수 포인터를 생성합니다. `4d61726b646f776e2e436f64652822222c2022406366756e6374696f6e2229_40726566`의 인자는:

1. 줄리아 함수
2. 함수의 반환 유형
3. 함수 시그니처에 해당하는 입력 유형의 튜플

!!! note
    `@ccall`와 마찬가지로, 반환 유형과 입력 유형은 리터럴 상수여야 합니다.


!!! note
    현재 플랫폼 기본 C 호출 규약만 지원됩니다. 이는 `@cfunction`으로 생성된 포인터가 32비트 Windows에서 WINAPI가 `stdcall` 함수를 기대하는 호출에 사용할 수 없지만, WIN64에서는 사용할 수 있음을 의미합니다(여기서 `stdcall`은 C 호출 규약과 통합됩니다).


!!! note
    `@cfunction`를 통해 노출된 콜백 함수는 오류를 발생시켜서는 안 됩니다. 이는 예기치 않게 Julia 런타임으로 제어를 반환하게 하여 프로그램을 정의되지 않은 상태로 남길 수 있습니다.


전형적인 예는 표준 C 라이브러리의 `qsort` 함수로, 다음과 같이 선언됩니다:

```c
void qsort(void *base, size_t nitems, size_t size,
           int (*compare)(const void*, const void*));
```

`base` 인자는 길이가 `nitems`인 배열에 대한 포인터로, 각 요소는 `size` 바이트입니다. `compare`는 두 요소 `a`와 `b`에 대한 포인터를 받아들이고, `a`가 `b`보다 앞에/뒤에 나타나야 하는 경우 0보다 작은/큰 정수를 반환하며 (어떤 순서도 허용되는 경우 0을 반환합니다).

이제, 우리가 정렬하고자 하는 값들의 1차원 배열 `A`가 있다고 가정해 보겠습니다. 우리는 `qsort` 함수를 사용하여 정렬할 것입니다(줄리아의 내장 `sort` 함수 대신). `qsort`를 호출하고 인수를 전달하기 전에, 비교 함수를 작성해야 합니다:

```jldoctest mycompare
julia> function mycompare(a, b)::Cint
           return (a < b) ? -1 : ((a > b) ? +1 : 0)
       end;
```

`qsort`는 C `int`를 반환하는 비교 함수를 기대하므로, 반환 유형을 `Cint`로 주석을 달아야 합니다.

이 함수를 C로 전달하기 위해 매크로 `@cfunction`을 사용하여 그 주소를 얻습니다:

```jldoctest mycompare
julia> mycompare_c = @cfunction(mycompare, Cint, (Ref{Cdouble}, Ref{Cdouble}));
```

[`@cfunction`](@ref)는 세 개의 인자를 요구합니다: 줄리아 함수(`mycompare`), 반환 타입(`Cint`), 그리고 입력 인자 타입의 리터럴 튜플, 이 경우 `Cdouble`([`Float64`](@ref)) 요소로 배열을 정렬하기 위한 것입니다.

최종 `qsort` 호출은 다음과 같습니다:

```jldoctest mycompare
julia> A = [1.3, -2.7, 4.4, 3.1];

julia> @ccall qsort(A::Ptr{Cdouble}, length(A)::Csize_t, sizeof(eltype(A))::Csize_t, mycompare_c::Ptr{Cvoid})::Cvoid

julia> A
4-element Vector{Float64}:
 -2.7
  1.3
  3.1
  4.4
```

예제에서 보여주듯이, 원래의 Julia 배열 `A`는 이제 정렬되었습니다: `[-2.7, 1.3, 3.1, 4.4]`. Julia [takes care of converting the array to a `Ptr{Cdouble}`](@ref automatic-type-conversion)), 요소 유형의 크기를 바이트 단위로 계산하는 것과 같은 작업을 수행합니다.

재미로, `mycompare`에 `println("mycompare($a, $b)")` 라인을 삽입해 보세요. 이렇게 하면 `qsort`가 수행하는 비교를 볼 수 있고, 실제로 전달한 Julia 함수를 호출하고 있는지 확인할 수 있습니다.

## [Mapping C Types to Julia](@id mapping-c-types-to-julia)

선언된 C 타입과 Julia에서의 선언이 정확히 일치하는 것이 중요합니다. 불일치가 발생하면 한 시스템에서 제대로 작동하는 코드가 다른 시스템에서는 실패하거나 불확실한 결과를 생성할 수 있습니다.

C 함수 호출 과정에서 C 헤더 파일이 어디에서도 사용되지 않음을 유의하십시오: Julia 유형과 호출 서명이 C 헤더 파일의 내용을 정확하게 반영하도록 하는 것은 귀하의 책임입니다.[^2]

### [Automatic Type Conversion](@id automatic-type-conversion)

줄리아는 각 인수를 지정된 유형으로 변환하기 위해 [`Base.cconvert`](@ref) 함수에 대한 호출을 자동으로 삽입합니다. 예를 들어, 다음 호출:

```julia
@ccall "libfoo".foo(x::Int32, y::Float64)::Cvoid
```

이렇게 작성된 것처럼 행동할 것입니다:

```julia
c_x = Base.cconvert(Int32, x)
c_y = Base.cconvert(Float64, y)
GC.@preserve c_x c_y begin
    @ccall "libfoo".foo(
        Base.unsafe_convert(Int32, c_x)::Int32,
        Base.unsafe_convert(Float64, c_y)::Float64
    )::Cvoid
end
```

[`Base.cconvert`](@ref)는 일반적으로 [`convert`](@ref)를 호출하지만, C에 전달하기에 더 적합한 임의의 새로운 객체를 반환하도록 정의할 수 있습니다. 이는 C 코드에서 접근할 메모리의 모든 할당을 수행하는 데 사용되어야 합니다. 예를 들어, 이는 객체(예: 문자열)의 `Array`를 포인터 배열로 변환하는 데 사용됩니다.

[`Base.unsafe_convert`](@ref)는 [`Ptr`](@ref) 유형으로 변환하는 기능을 처리합니다. 이는 객체를 네이티브 포인터로 변환하면 가비지 컬렉터로부터 객체가 숨겨져 조기에 해제될 수 있기 때문에 안전하지 않은 것으로 간주됩니다.

### Type Correspondences

먼저, 관련된 줄리아 타입 용어를 검토해 봅시다:

| Syntax / Keyword        | Example                                    | Description                                                                                                                                                                                                                                                       |
|:----------------------- |:------------------------------------------ |:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `mutable struct`        | `BitSet`                                   | "Leaf Type" :: A group of related data that includes a type-tag, is managed by the Julia GC, and is defined by object-identity. The type parameters of a leaf type must be fully defined (no `TypeVars` are allowed) in order for the instance to be constructed. |
| `abstract type`         | `Any`, `AbstractArray{T, N}`, `Complex{T}` | "Super Type" :: A super-type (not a leaf-type) that cannot be instantiated, but can be used to describe a group of types.                                                                                                                                         |
| `T{A}`                  | `Vector{Int}`                              | "Type Parameter" :: A specialization of a type (typically used for dispatch or storage optimization).                                                                                                                                                             |
|                         |                                            | "TypeVar" :: The `T` in the type parameter declaration is referred to as a TypeVar (short for type variable).                                                                                                                                                     |
| `primitive type`        | `Int`, `Float64`                           | "Primitive Type" :: A type with no fields, but a size. It is stored and defined by-value.                                                                                                                                                                         |
| `struct`                | `Pair{Int, Int}`                           | "Struct" :: A type with all fields defined to be constant. It is defined by-value, and may be stored with a type-tag.                                                                                                                                             |
|                         | `ComplexF64` (`isbits`)                    | "Is-Bits"   :: A `primitive type`, or a `struct` type where all fields are other `isbits` types. It is defined by-value, and is stored without a type-tag.                                                                                                        |
| `struct ...; end`       | `nothing`                                  | "Singleton" :: a Leaf Type or Struct with no fields.                                                                                                                                                                                                              |
| `(...)` or `tuple(...)` | `(1, 2, 3)`                                | "Tuple" :: an immutable data-structure similar to an anonymous struct type, or a constant array. Represented as either an array or a struct.                                                                                                                      |

### [Bits Types](@id man-bits-types)

특별한 유형이 몇 가지 있으며, 다른 유형이 동일하게 동작하도록 정의될 수 없다는 점에 유의해야 합니다:

  * `Float32`

    C(또는 Fortran의 `REAL*4`)의 `float` 타입과 정확히 일치합니다.
  * `Float64`

    C(또는 Fortran의 `REAL*8`)에서 `double` 유형과 정확히 일치합니다.
  * `복소수F32`

    C(또는 Fortran의 `COMPLEX*8`)에서 `complex float` 유형과 정확히 일치합니다.
  * `복소수F64`

    C(또는 Fortran의 `COMPLEX*16`)에서 `complex double` 유형과 정확히 일치합니다.
  * `서명됨`

    정확히 C의 `signed` 타입 주석(또는 Fortran의 모든 `INTEGER` 타입)에 해당합니다. [`Signed`](@ref)의 하위 타입이 아닌 모든 Julia 타입은 부호 없는 것으로 간주됩니다.

  * `Ref{T}`

    `Ptr{T}`처럼 동작하며 Julia GC를 통해 메모리를 관리할 수 있습니다.

  * `Array{T,N}`

    배열이 C에 `Ptr{T}` 인수로 전달될 때, 재해석 캐스트되지 않습니다: Julia는 배열의 요소 유형이 `T`와 일치해야 하며, 첫 번째 요소의 주소가 전달됩니다.

    따라서, `Array`에 잘못된 형식의 데이터가 포함되어 있다면, `trunc.(Int32, A)`와 같은 호출을 사용하여 명시적으로 변환해야 합니다.

    배열 `A`를 데이터를 미리 변환하지 않고(예: `Float64` 배열을 해석되지 않은 바이트에서 작동하는 함수에 전달하기 위해) 다른 유형의 포인터로 전달하려면, 인수를 `Ptr{Cvoid}`로 선언할 수 있습니다.

    배열의 eltype `Ptr{T}`가 `Ptr{Ptr{T}}` 인수로 전달되면, [`Base.cconvert`](@ref)는 각 요소가 자신의 `4d61726b646f776e2e436f64652822222c2022426173652e63636f6e766572742229_40726566` 버전으로 대체된 배열의 널 종료 복사본을 먼저 만들려고 시도합니다. 이를 통해 예를 들어, `Vector{String}` 유형의 `argv` 포인터 배열을 `Ptr{Ptr{Cchar}}` 유형의 인수로 전달할 수 있습니다.

현재 지원하는 모든 시스템에서 기본 C/C++ 값 유형은 다음과 같이 Julia 유형으로 변환될 수 있습니다. 모든 C 유형은 C로 접두사가 붙은 동일한 이름의 해당 Julia 유형을 가지고 있습니다. 이는 이식 가능한 코드를 작성할 때 도움이 될 수 있습니다(그리고 C의 `int`가 Julia의 `Int`와 같지 않다는 것을 기억하는 데 도움이 됩니다).

**시스템 독립형 타입**

| C name                                                  | Fortran name             | Standard Julia Alias | Julia Base Type                                                                                             |
|:------------------------------------------------------- |:------------------------ |:-------------------- |:----------------------------------------------------------------------------------------------------------- |
| `unsigned char`                                         | `CHARACTER`              | `Cuchar`             | `UInt8`                                                                                                     |
| `bool` (_Bool in C99+)                                  |                          | `Cuchar`             | `UInt8`                                                                                                     |
| `short`                                                 | `INTEGER*2`, `LOGICAL*2` | `Cshort`             | `Int16`                                                                                                     |
| `unsigned short`                                        |                          | `Cushort`            | `UInt16`                                                                                                    |
| `int`, `BOOL` (C, typical)                              | `INTEGER*4`, `LOGICAL*4` | `Cint`               | `Int32`                                                                                                     |
| `unsigned int`                                          |                          | `Cuint`              | `UInt32`                                                                                                    |
| `long long`                                             | `INTEGER*8`, `LOGICAL*8` | `Clonglong`          | `Int64`                                                                                                     |
| `unsigned long long`                                    |                          | `Culonglong`         | `UInt64`                                                                                                    |
| `intmax_t`                                              |                          | `Cintmax_t`          | `Int64`                                                                                                     |
| `uintmax_t`                                             |                          | `Cuintmax_t`         | `UInt64`                                                                                                    |
| `float`                                                 | `REAL*4i`                | `Cfloat`             | `Float32`                                                                                                   |
| `double`                                                | `REAL*8`                 | `Cdouble`            | `Float64`                                                                                                   |
| `complex float`                                         | `COMPLEX*8`              | `ComplexF32`         | `Complex{Float32}`                                                                                          |
| `complex double`                                        | `COMPLEX*16`             | `ComplexF64`         | `Complex{Float64}`                                                                                          |
| `ptrdiff_t`                                             |                          | `Cptrdiff_t`         | `Int`                                                                                                       |
| `ssize_t`                                               |                          | `Cssize_t`           | `Int`                                                                                                       |
| `size_t`                                                |                          | `Csize_t`            | `UInt`                                                                                                      |
| `void`                                                  |                          |                      | `Cvoid`                                                                                                     |
| `void` and `[[noreturn]]` or `_Noreturn`                |                          |                      | `Union{}`                                                                                                   |
| `void*`                                                 |                          |                      | `Ptr{Cvoid}` (or similarly `Ref{Cvoid}`)                                                                    |
| `T*` (where T represents an appropriately defined type) |                          |                      | `Ref{T}` (T may be safely mutated only if T is an isbits type)                                              |
| `char*` (or `char[]`, e.g. a string)                    | `CHARACTER*N`            |                      | `Cstring` if null-terminated, or `Ptr{UInt8}` if not                                                        |
| `char**` (or `*char[]`)                                 |                          |                      | `Ptr{Ptr{UInt8}}`                                                                                           |
| `jl_value_t*` (any Julia Type)                          |                          |                      | `Any`                                                                                                       |
| `jl_value_t* const*` (a reference to a Julia value)     |                          |                      | `Ref{Any}` (const, since mutation would require a write barrier, which is not possible to insert correctly) |
| `va_arg`                                                |                          |                      | Not supported                                                                                               |
| `...` (variadic function specification)                 |                          |                      | `T...` (where `T` is one of the above types, when using the `ccall` function)                               |
| `...` (variadic function specification)                 |                          |                      | `; va_arg1::T, va_arg2::S, etc.` (only supported with `@ccall` macro)                                       |

[`Cstring`](@ref) 유형은 본질적으로 `Ptr{UInt8}`의 동의어입니다. 단, `Cstring`으로 변환할 때 Julia 문자열에 임베디드 널 문자가 포함되어 있으면 오류가 발생합니다(이는 C 루틴이 널을 종료 문자로 처리할 경우 문자열이 조용히 잘리게 됩니다). 널 종료를 가정하지 않는 C 루틴에 `char*`를 전달하는 경우(예: 명시적인 문자열 길이를 전달하는 경우) 또는 Julia 문자열에 널이 포함되어 있지 않다고 확신하고 검사를 건너뛰고 싶다면 `Ptr{UInt8}`를 인수 유형으로 사용할 수 있습니다. `Cstring`은 [`ccall`](@ref) 반환 유형으로도 사용할 수 있지만, 이 경우에는 명백히 추가 검사를 도입하지 않으며 호출의 가독성을 향상시키기 위한 것입니다.

**시스템 의존형**

| C name          | Standard Julia Alias | Julia Base Type                              |
|:--------------- |:-------------------- |:-------------------------------------------- |
| `char`          | `Cchar`              | `Int8` (x86, x86_64), `UInt8` (powerpc, arm) |
| `long`          | `Clong`              | `Int` (UNIX), `Int32` (Windows)              |
| `unsigned long` | `Culong`             | `UInt` (UNIX), `UInt32` (Windows)            |
| `wchar_t`       | `Cwchar_t`           | `Int32` (UNIX), `UInt16` (Windows)           |

!!! note
    Fortran을 호출할 때, 모든 입력은 힙 또는 스택에 할당된 값에 대한 포인터로 전달되어야 하므로, 위의 모든 타입 대응은 해당 타입 사양 주위에 추가적인 `Ptr{..}` 또는 `Ref{..}` 래퍼를 포함해야 합니다.


!!! warning
    문자열 인수(`char*`)의 경우, 줄리아 타입은 `Cstring`이어야 합니다(널 종료 데이터가 예상되는 경우). 그렇지 않으면 `Ptr{Cchar}` 또는 `Ptr{UInt8}` 중 하나여야 합니다(이 두 포인터 타입은 동일한 효과를 가집니다). 배열 인수(`T[]` 또는 `T*`)의 경우에도 줄리아 타입은 다시 `Ptr{T}`여야 하며, `Vector{T}`가 아닙니다.


!!! warning
    줄리아의 `Char` 타입은 32비트로, 모든 플랫폼에서 와이드 캐릭터 타입(`wchar_t` 또는 `wint_t`)과 동일하지 않습니다.


!!! warning
    `Union{}`의 반환 유형은 함수가 반환하지 않음을 의미합니다. 즉, C++11의 `[[noreturn]]` 또는 C11의 `_Noreturn`과 같습니다 (예: `jl_throw` 또는 `longjmp`). 반환값이 없는 함수(`void`)에 대해서는 이 유형을 사용하지 마십시오. 그런 경우에는 대신 `Cvoid`를 사용하십시오.


!!! note
    `wchar_t*` 인수의 경우, Julia 타입은 [`Cwstring`](@ref) (C 루틴이 널 종료 문자열을 기대하는 경우) 또는 그렇지 않으면 `Ptr{Cwchar_t}` 여야 합니다. 또한 Julia의 UTF-8 문자열 데이터는 내부적으로 널 종료되어 있으므로, 복사 없이 널 종료 데이터를 기대하는 C 함수에 전달할 수 있습니다 (하지만 `Cwstring` 타입을 사용하면 문자열 자체에 널 문자가 포함되어 있을 경우 오류가 발생합니다).


!!! note
    C 함수는 `char**` 유형의 인수를 사용하여 호출할 수 있으며, Julia에서는 `Ptr{Ptr{UInt8}}` 유형을 사용하여 호출할 수 있습니다. 예를 들어, 다음과 같은 형태의 C 함수:

    ```c
    int main(int argc, char **argv);
    ```

    다음 Julia 코드를 통해 호출될 수 있습니다:

    ```julia
    argv = [ "a.out", "arg1", "arg2" ]
    @ccall main(length(argv)::Int32, argv::Ptr{Ptr{UInt8}})::Int32
    ```


!!! note
    Fortran 함수가 가변 길이 문자열인 `character(len=*)` 유형을 사용할 때 문자열 길이는 *숨겨진 인수*로 제공됩니다. 이러한 인수의 유형과 위치는 컴파일러에 따라 다르며, 컴파일러 공급업체는 일반적으로 `Csize_t`를 유형으로 사용하고 숨겨진 인수를 인수 목록의 끝에 추가하는 것을 기본값으로 설정합니다. 일부 컴파일러(GNU)의 경우 이 동작은 고정되어 있지만, 다른 컴파일러(Intel, PGI)는 선택적으로 숨겨진 인수를 문자 인수 바로 뒤에 배치할 수 있도록 허용합니다. 예를 들어, 다음과 같은 형태의 Fortran 서브루틴

    ```fortran
    subroutine test(str1, str2)
    character(len=*) :: str1,str2
    ```

    다음 Julia 코드를 통해 호출할 수 있으며, 길이가 추가됩니다.

    ```julia
    str1 = "foo"
    str2 = "bar"
    ccall(:test, Cvoid, (Ptr{UInt8}, Ptr{UInt8}, Csize_t, Csize_t),
                        str1, str2, sizeof(str1), sizeof(str2))
    ```


!!! warning
    Fortran 컴파일러는 포인터, 가정된 형태(`:`) 및 가정된 크기(`*`) 배열에 대해 다른 숨겨진 인수를 추가할 *수 있습니다*. 이러한 동작은 `ISO_C_BINDING`을 사용하고 서브루틴 정의에 `bind(c)`를 포함시킴으로써 피할 수 있으며, 이는 상호 운용 가능한 코드에 강력히 권장됩니다. 이 경우 숨겨진 인수가 없지만, 일부 언어 기능(예: `character(len=1)`만 문자열을 전달하는 것이 허용됨)의 대가를 치르게 됩니다.


!!! note
    C 함수가 `Cvoid`를 반환하도록 선언되면, Julia에서는 `nothing` 값을 반환합니다.


### Struct Type Correspondences

C나 Fortran90의 `TYPE` (또는 F77의 일부 변형에서 `STRUCTURE` / `RECORD`)와 같은 복합 유형은 동일한 필드 레이아웃을 가진 `struct` 정의를 생성하여 Julia에서 미러링할 수 있습니다.

재귀적으로 사용될 때, `isbits` 타입은 인라인으로 저장됩니다. 다른 모든 타입은 데이터에 대한 포인터로 저장됩니다. C에서 다른 구조체 내부에 값으로 사용되는 구조체를 미러링할 때, 필드를 수동으로 복사하려고 시도하지 않는 것이 중요합니다. 이렇게 하면 올바른 필드 정렬이 유지되지 않습니다. 대신, `isbits` 구조체 타입을 선언하고 그것을 사용해야 합니다. 이름이 없는 구조체는 Julia로의 변환에서 불가능합니다.

줄리아에서는 패킹된 구조체 및 공용체 선언이 지원되지 않습니다.

`union`의 근사값을 얻으려면, 사전에 가장 큰 크기를 가질 필드를 알고 있어야 합니다(패딩을 포함할 수 있음). 필드를 Julia로 변환할 때, Julia 필드를 해당 유형만으로 선언하십시오.

매개변수의 배열은 `NTuple`로 표현할 수 있습니다. 예를 들어, C 표기법으로 작성된 구조체는 다음과 같습니다.

```c
struct B {
    int A[3];
};

b_a_2 = B.A[2];
```

줄리아로 작성할 수 있습니다.

```julia
struct B
    A::NTuple{3, Cint}
end

b_a_2 = B.A[3]  # note the difference in indexing (1-based in Julia, 0-based in C)
```

크기 미정 배열(C99 준수 가변 길이 구조체는 `[]` 또는 `[0]`로 지정됨)은 직접 지원되지 않습니다. 이러한 배열을 처리하는 가장 좋은 방법은 바이트 오프셋을 직접 다루는 것입니다. 예를 들어, C 라이브러리가 적절한 문자열 유형을 선언하고 이에 대한 포인터를 반환하는 경우:

```c
struct String {
    int strlen;
    char data[];
};
```

줄리아에서는 문자열의 일부에 독립적으로 접근하여 해당 문자열의 복사본을 만들 수 있습니다:

```julia
str = from_c::Ptr{Cvoid}
len = unsafe_load(Ptr{Cint}(str))
unsafe_string(str + Core.sizeof(Cint), len)
```

### Type Parameters

`@ccall` 및 `@cfunction`에 대한 타입 인수는 사용이 정의될 때 정적으로 평가됩니다. 따라서 이들은 변수 대신 리터럴 튜플의 형태를 가져야 하며, 지역 변수를 참조할 수 없습니다.

이것은 이상한 제한처럼 들릴 수 있지만, C는 Julia와 같은 동적 언어가 아니기 때문에 그 함수는 정적으로 알려진 고정된 시그니처를 가진 인수 유형만 허용한다는 점을 기억하세요.

그러나 C ABI를 계산하기 위해서는 타입 레이아웃이 정적으로 알려져야 하며, 함수의 정적 매개변수는 이 정적 환경의 일부로 간주됩니다. 함수의 정적 매개변수는 타입 레이아웃에 영향을 미치지 않는 한 호출 서명에서 타입 매개변수로 사용될 수 있습니다. 예를 들어, `f(x::T) where {T} = @ccall valid(x::Ptr{T})::Ptr{T}`는 유효합니다. 왜냐하면 `Ptr`는 항상 단어 크기의 원시 타입이기 때문입니다. 그러나 `g(x::T) where {T} = @ccall notvalid(x::T)::T`는 유효하지 않습니다. 왜냐하면 `T`의 타입 레이아웃이 정적으로 알려져 있지 않기 때문입니다.

### SIMD Values

참고: 이 기능은 현재 64비트 x86 및 AArch64 플랫폼에서만 구현되어 있습니다.

C/C++ 루틴에 인수나 반환 값으로 네이티브 SIMD 유형이 있는 경우, 해당하는 Julia 유형은 SIMD 유형에 자연스럽게 매핑되는 `VecElement`의 동질적인 튜플입니다. 구체적으로:

>   * 튜플은 SIMD 타입과 동일한 크기여야 합니다. 예를 들어, x86에서 `__m128`을 나타내는 튜플은 16바이트의 크기를 가져야 합니다.
>   * 튜플의 요소 유형은 `VecElement{T}`의 인스턴스여야 하며, 여기서 `T`는 1, 2, 4 또는 8 바이트의 원시 유형입니다.


예를 들어, AVX 인트린식을 사용하는 이 C 루틴을 고려해 보십시오:

```c
#include <immintrin.h>

__m256 dist( __m256 a, __m256 b ) {
    return _mm256_sqrt_ps(_mm256_add_ps(_mm256_mul_ps(a, a),
                                        _mm256_mul_ps(b, b)));
}
```

다음 Julia 코드는 `ccall`을 사용하여 `dist`를 호출합니다:

```julia
const m256 = NTuple{8, VecElement{Float32}}

a = m256(ntuple(i -> VecElement(sin(Float32(i))), 8))
b = m256(ntuple(i -> VecElement(cos(Float32(i))), 8))

function call_dist(a::m256, b::m256)
    @ccall "libdist".dist(a::m256, b::m256)::m256
end

println(call_dist(a,b))
```

호스트 머신은 필수 SIMD 레지스터를 갖추고 있어야 합니다. 예를 들어, 위의 코드는 AVX 지원이 없는 호스트에서는 작동하지 않습니다.

### Memory Ownership

**`malloc`/`free`**

메모리 할당 및 해제는 사용 중인 라이브러리의 적절한 정리 루틴을 호출하여 처리해야 하며, 이는 모든 C 프로그램과 마찬가지입니다. Julia에서 [`Libc.free`](@ref)로부터 받은 객체를 해제하려고 하지 마십시오. 이는 잘못된 라이브러리를 통해 `free` 함수가 호출되어 프로세스가 중단될 수 있습니다. 반대로, Julia에서 할당된 객체를 외부 라이브러리에서 해제하도록 전달하는 것도 마찬가지로 유효하지 않습니다.

### When to use `T`, `Ptr{T}` and `Ref{T}`

In Julia code wrapping calls to external C routines, ordinary (non-pointer) data should be declared to be of type `T` inside the `@ccall`, as they are passed by value. For C code accepting pointers, [`Ref{T}`](@ref) should generally be used for the types of input arguments, allowing the use of pointers to memory managed by either Julia or C through the implicit call to [`Base.cconvert`](@ref). In contrast, pointers returned by the C function called should be declared to be of the output type [`Ptr{T}`](@ref), reflecting that the memory pointed to is managed by C only. Pointers contained in C structs should be represented as fields of type `Ptr{T}` within the corresponding Julia struct types designed to mimic the internal structure of corresponding C structs.

줄리아 코드에서 외부 포트란 루틴을 호출할 때, 모든 입력 인자는 `Ref{T}` 유형으로 선언해야 합니다. 포트란은 모든 변수를 메모리 위치에 대한 포인터로 전달하기 때문입니다. 반환 유형은 포트란 서브루틴의 경우 `Cvoid`이거나, 유형 `T`를 반환하는 포트란 함수의 경우 `T`여야 합니다.

## Mapping C Functions to Julia

### `@ccall` / `@cfunction` argument translation guide

C 인수 목록을 Julia로 변환하기 위해:

  * `T`, 여기서 `T`는 기본 데이터 유형 중 하나입니다: `char`, `int`, `long`, `short`, `float`, `double`, `complex`, `enum` 또는 이들의 `typedef` 동등물

      * `T`, 여기서 `T`는 위의 표에 따른 동등한 Julia Bits Type입니다.
      * `T`가 `enum`인 경우, 인수 유형은 `Cint` 또는 `Cuint`와 동일해야 합니다.
      * 인수 값이 복사됩니다 (값에 의해 전달됨)
  * `struct T` (구조체에 대한 typedef 포함)

      * `T`, 여기서 `T`는 Julia 리프 타입입니다.
      * 인수 값이 복사됩니다 (값에 의해 전달됨)
  * `void*`

      * 이 매개변수가 어떻게 사용되는지에 따라 다릅니다. 먼저 이것을 의도된 포인터 유형으로 번역한 다음, 이 목록의 나머지 규칙을 사용하여 줄리아 동등성을 결정합니다.
      * 이 인자는 실제로 알 수 없는 포인터라면 `Ptr{Cvoid}`로 선언될 수 있습니다.
  * `jl_value_t*`

      * `모든`
      * 인수 값은 유효한 줄리아 객체여야 합니다.
  * `jl_value_t* const*`

      * `Ref{아무}`
      * 인수 목록은 유효한 Julia 객체여야 합니다 (또는 `C_NULL`).
      * 출력 매개변수로 사용할 수 없으며, 사용자가 객체를 GC(가비지 컬렉션)로 보존하도록 별도로 조치할 수 없는 경우입니다.
  * `T*`

      * `Ref{T}`, 여기서 `T`는 `T`에 해당하는 Julia 타입입니다.
      * 인수 값은 `inlinealloc` 유형일 경우 복사됩니다(여기에는 `isbits`가 포함됨). 그렇지 않으면 값은 유효한 줄리아 객체여야 합니다.
  * `T (*)(...)` (예: 함수에 대한 포인터)

      * `Ptr{Cvoid}` (이 포인터를 생성하려면 [`@cfunction`](@ref)를 명시적으로 사용해야 할 수 있습니다)
  * `...` (예: 가변 인자)

      * [for `ccall`]: `T...`, 여기서 `T`는 나머지 모든 인수의 단일 Julia 타입입니다.
      * [for `@ccall`]: `; va_arg1::T, va_arg2::S, etc`, 여기서 `T`와 `S`는 줄리아 타입입니다 (즉, 일반 인수와 가변 인수를 `;`로 구분합니다)
      * 현재 `@cfunction`에 의해 지원되지 않음
  * `va_arg`

      * `ccall` 또는 `@cfunction`에 의해 지원되지 않음

### `@ccall` / `@cfunction` return type translation guide

C 반환 유형을 줄리아로 변환하기 위해:

  * `무효`

      * `Cvoid` (이것은 단일 인스턴스 `nothing::Cvoid`를 반환합니다)
  * `T`, 여기서 `T`는 기본 데이터 유형 중 하나입니다: `char`, `int`, `long`, `short`, `float`, `double`, `complex`, `enum` 또는 이들의 `typedef` 동등물

      * `T`, 여기서 `T`는 위의 표에 따른 동등한 Julia Bits Type입니다.
      * `T`가 `enum`인 경우, 인수 유형은 `Cint` 또는 `Cuint`와 동일해야 합니다.
      * 인수 값이 복사됩니다 (값에 의해 반환됨)
  * `struct T` (구조체에 대한 typedef 포함)

      * `T`, 여기서 `T`는 Julia Leaf Type입니다.
      * 인수 값이 복사됩니다 (값에 의해 반환됨)
  * `void*`

      * 이 매개변수가 어떻게 사용되는지에 따라 다릅니다. 먼저 이것을 의도된 포인터 유형으로 번역한 다음, 이 목록의 나머지 규칙을 사용하여 줄리아 동등성을 결정합니다.
      * 이 인자는 실제로 알 수 없는 포인터라면 `Ptr{Cvoid}`로 선언될 수 있습니다.
  * `jl_value_t*`

      * `모든`
      * 인수 값은 유효한 줄리아 객체여야 합니다.
  * `jl_value_t**`

      * `Ptr{Any}` (`Ref{Any}`는 반환 타입으로 유효하지 않습니다)
  * `T*`

      * 메모리가 이미 Julia에 의해 소유되었거나 `isbits` 타입이며 널이 아님이 알려진 경우:

          * `Ref{T}`, 여기서 `T`는 `T`에 해당하는 Julia 타입입니다.
          * `Ref{Any}`의 반환 유형은 유효하지 않습니다. `Any`(즉, `jl_value_t*`에 해당) 또는 `Ptr{Any}`(즉, `jl_value_t**`에 해당) 중 하나여야 합니다.
          * C **절대** `T`가 `isbits` 타입인 경우 `Ref{T}`를 통해 반환된 메모리를 수정해서는 안 됩니다.
      * C가 메모리를 소유하는 경우:

          * `Ptr{T}`, 여기서 `T`는 `T`에 해당하는 Julia 타입입니다.
  * `T (*)(...)` (예: 함수에 대한 포인터)

      * `Ptr{Cvoid}`를 사용하여 이를 Julia에서 직접 호출하려면, 이를 `@ccall`의 첫 번째 인수로 전달해야 합니다. [Indirect Calls](@ref)를 참조하세요.

### Passing Pointers for Modifying Inputs

C는 여러 개의 반환 값을 지원하지 않기 때문에, 종종 C 함수는 함수가 수정할 데이터에 대한 포인터를 받습니다. `@ccall` 내에서 이를 수행하려면, 먼저 적절한 유형의 [`Ref{T}`](@ref) 안에 값을 캡슐화해야 합니다. 이 `Ref` 객체를 인수로 전달하면, Julia는 자동으로 캡슐화된 데이터에 대한 C 포인터를 전달합니다:

```julia
width = Ref{Cint}(0)
range = Ref{Cfloat}(0)
@ccall foo(width::Ref{Cint}, range::Ref{Cfloat})::Cvoid
```

반환 시, `width`와 `range`의 내용은 `foo`에 의해 변경되었다면 `width[]`와 `range[]`를 통해 검색할 수 있습니다. 즉, 이들은 제로 차원 배열처럼 작동합니다.

## C Wrapper Examples

간단한 `Ptr` 타입을 반환하는 C 래퍼의 예제로 시작해 보겠습니다:

```julia
mutable struct gsl_permutation
end

# The corresponding C signature is
#     gsl_permutation * gsl_permutation_alloc (size_t n);
function permutation_alloc(n::Integer)
    output_ptr = @ccall "libgsl".gsl_permutation_alloc(n::Csize_t)::Ptr{gsl_permutation}
    if output_ptr == C_NULL # Could not allocate memory
        throw(OutOfMemoryError())
    end
    return output_ptr
end
```

[GNU Scientific Library](https://www.gnu.org/software/gsl/) (여기서는 `:libgsl`을 통해 접근할 수 있다고 가정함) 은 C 함수 `gsl_permutation_alloc`의 반환 타입으로 불투명 포인터 `gsl_permutation *`를 정의합니다. 사용자 코드가 `gsl_permutation` 구조체 내부를 들여다볼 필요가 없기 때문에, 해당하는 줄리아 래퍼는 내부 필드가 없는 새로운 타입 선언 `gsl_permutation`만 필요하며, 이 타입은 `Ptr` 타입의 타입 매개변수에 배치되는 것이 유일한 목적입니다. [`ccall`](@ref)의 반환 타입은 `Ptr{gsl_permutation}`으로 선언되며, 이는 `output_ptr`이 가리키는 메모리가 C에 의해 제어되기 때문입니다.

입력 `n`은 값으로 전달되므로 함수의 입력 시그니처는 `::Csize_t`로 간단히 선언되며 `Ref`나 `Ptr`이 필요하지 않습니다. (만약 래퍼가 Fortran 함수를 호출하고 있었다면, 해당 함수의 입력 시그니처는 `::Ref{Csize_t}`가 되었을 것입니다. 왜냐하면 Fortran 변수는 포인터로 전달되기 때문입니다.) 또한, `n`은 `Csize_t` 정수로 변환 가능한 모든 유형이 될 수 있습니다; [`ccall`](@ref)는 암묵적으로 [`Base.cconvert(Csize_t, n)`](@ref)를 호출합니다.

여기 해당 소멸자를 감싸는 두 번째 예제가 있습니다:

```julia
# The corresponding C signature is
#     void gsl_permutation_free (gsl_permutation * p);
function permutation_free(p::Ptr{gsl_permutation})
    @ccall "libgsl".gsl_permutation_free(p::Ptr{gsl_permutation})::Cvoid
end
```

여기 줄리아 배열을 전달하는 세 번째 예제가 있습니다:

```julia
# The corresponding C signature is
#    int gsl_sf_bessel_Jn_array (int nmin, int nmax, double x,
#                                double result_array[])
function sf_bessel_Jn_array(nmin::Integer, nmax::Integer, x::Real)
    if nmax < nmin
        throw(DomainError())
    end
    result_array = Vector{Cdouble}(undef, nmax - nmin + 1)
    errorcode = @ccall "libgsl".gsl_sf_bessel_Jn_array(
                    nmin::Cint, nmax::Cint, x::Cdouble, result_array::Ref{Cdouble})::Cint
    if errorcode != 0
        error("GSL error code $errorcode")
    end
    return result_array
end
```

C 함수 wrapped는 정수 오류 코드를 반환하며, Bessel J 함수의 실제 평가 결과는 Julia 배열 `result_array`를 채웁니다. 이 변수는 `Ref{Cdouble}`로 선언되며, 그 메모리는 Julia에 의해 할당되고 관리됩니다. [`Base.cconvert(Ref{Cdouble}, result_array)`](@ref)에 대한 암묵적인 호출은 Julia 포인터를 C에서 이해할 수 있는 형태로 Julia 배열 데이터 구조로 언팩합니다.

## Fortran Wrapper Example

다음 예제는 `ccall`을 사용하여 공통 Fortran 라이브러리(libBLAS)의 함수를 호출하여 내적을 계산합니다. 인수 매핑이 위와 약간 다르다는 점에 유의하십시오. Julia에서 Fortran으로 매핑해야 합니다. 모든 인수 유형에 대해 `Ref` 또는 `Ptr`을 지정합니다. 이 이름 맹글링 규칙은 특정 Fortran 컴파일러 및 운영 체제에 따라 다를 수 있으며 문서화되어 있지 않을 가능성이 높습니다. 그러나 각 인수를 `Ref`(또는 동등한 경우 `Ptr`)로 감싸는 것은 Fortran 컴파일러 구현의 일반적인 요구 사항입니다.

```julia
function compute_dot(DX::Vector{Float64}, DY::Vector{Float64})
    @assert length(DX) == length(DY)
    n = length(DX)
    incx = incy = 1
    product = @ccall "libLAPACK".ddot(
        n::Ref{Int32}, DX::Ptr{Float64}, incx::Ref{Int32}, DY::Ptr{Float64}, incy::Ref{Int32})::Float64
    return product
end
```

## Garbage Collection Safety

데이터를 `@ccall`에 전달할 때는 [`pointer`](@ref) 함수를 사용하는 것을 피하는 것이 좋습니다. 대신 [`Base.cconvert`](@ref) 메서드를 정의하고 변수를 `@ccall`에 직접 전달하세요. `@ccall`은 모든 인수가 호출이 반환될 때까지 가비지 컬렉션에서 보존되도록 자동으로 정리합니다. C API가 Julia에 의해 할당된 메모리에 대한 참조를 저장할 경우, `@ccall`이 반환된 후에도 객체가 가비지 컬렉터에 보이도록 해야 합니다. 이를 수행하는 권장 방법은 이러한 값을 보관하기 위해 `Array{Ref,1}` 유형의 전역 변수를 만드는 것입니다. C 라이브러리가 작업을 마쳤다고 알릴 때까지 이 값을 유지하세요.

줄리아 데이터에 대한 포인터를 생성할 때는 포인터 사용이 끝날 때까지 원본 데이터가 존재하는지 확인해야 합니다. [`unsafe_load`](@ref) 및 [`String`](@ref)와 같은 줄리아의 많은 메서드는 버퍼의 소유권을 가져오는 대신 데이터를 복사하므로, 원본 데이터를 안전하게 해제(또는 변경)할 수 있습니다. 줄리아에 영향을 주지 않습니다. 성능상의 이유로 [`unsafe_wrap`](@ref)는 기본 버퍼를 공유(또는 소유권을 가져오도록 지시할 수 있음)하는 주목할 만한 예외입니다.

가비지 수집기는 최종화의 순서를 보장하지 않습니다. 즉, `a`가 `b`에 대한 참조를 포함하고 있고 `a`와 `b` 모두 가비지 수집 대상이라면, `b`가 `a` 이후에 최종화될 것이라는 보장이 없습니다. `a`의 적절한 최종화가 `b`가 유효한 것에 의존한다면, 다른 방법으로 처리해야 합니다.

## Non-constant Function Specifications

일부 경우, 필요한 라이브러리의 정확한 이름이나 경로가 사전에 알려져 있지 않으며 실행 시간에 계산되어야 합니다. 이러한 경우를 처리하기 위해 라이브러리 구성 사양은 함수 호출이 될 수 있습니다. 예를 들어, `find_blas().dgemm`과 같습니다. 호출 표현식은 `ccall` 자체가 실행될 때 실행됩니다. 그러나 라이브러리 위치는 결정된 후에는 변경되지 않는 것으로 가정되므로 호출의 결과는 캐시되어 재사용될 수 있습니다. 따라서 표현식이 실행되는 횟수는 명시되지 않으며, 여러 호출에 대해 서로 다른 값을 반환하는 것은 명시되지 않은 동작을 초래합니다.

더 많은 유연성이 필요하다면, [`eval`](@ref)를 통해 단계적으로 함수 이름으로 계산된 값을 사용할 수 있습니다:

```julia
@eval @ccall "lib".$(string("a", "b"))()::Cint
```

이 표현식은 `string`을 사용하여 이름을 구성한 다음, 이 이름을 새로운 `@ccall` 표현식에 대체하여 평가합니다. `eval`은 최상위에서만 작동하므로, 이 표현식 내에서는 지역 변수가 사용 불가능합니다(값이 `$`로 대체되지 않는 한). 이러한 이유로 `eval`은 일반적으로 많은 유사한 함수를 포함하는 라이브러리를 래핑할 때와 같이 최상위 정의를 형성하는 데만 사용됩니다. [`@cfunction`](@ref)에 대한 유사한 예를 구성할 수 있습니다.

그러나 이렇게 하면 매우 느리고 메모리 누수가 발생하므로 일반적으로 이를 피하고 대신 계속 읽는 것이 좋습니다. 다음 섹션에서는 간접 호출을 사용하여 유사한 효과를 효율적으로 달성하는 방법에 대해 설명합니다.

## Indirect Calls

`@ccall`의 첫 번째 인수는 런타임에 평가되는 표현식일 수도 있습니다. 이 경우, 표현식은 호출할 네이티브 함수의 주소로 사용될 `Ptr`로 평가되어야 합니다. 이 동작은 첫 번째 `@ccall` 인수가 지역 변수, 함수 인수 또는 비상수 전역 변수와 같은 비상수에 대한 참조를 포함할 때 발생합니다.

예를 들어, `dlsym`을 통해 함수를 조회한 다음, 해당 세션에 대한 공유 참조에 캐시할 수 있습니다. 예를 들어:

```julia
macro dlsym(lib, func)
    z = Ref{Ptr{Cvoid}}(C_NULL)
    quote
        let zlocal = $z[]
            if zlocal == C_NULL
                zlocal = dlsym($(esc(lib))::Ptr{Cvoid}, $(esc(func)))::Ptr{Cvoid}
                $z[] = zlocal
            end
            zlocal
        end
    end
end

mylibvar = Libdl.dlopen("mylib")
@ccall $(@dlsym(mylibvar, "myfunc"))()::Cvoid
```

## Closure cfunctions

[`@cfunction`](@ref)의 첫 번째 인수는 `$`로 표시할 수 있으며, 이 경우 반환 값은 인수를 클로즈하는 `struct CFunction`이 됩니다. 이 반환 객체는 모든 사용이 완료될 때까지 유지되어야 합니다. cfunction 포인터의 내용과 코드는 이 참조가 삭제되고 atexit에서 [`finalizer`](@ref)를 통해 지워집니다. 이는 일반적으로 필요하지 않지만, 별도의 클로저 환경 매개변수를 제공하지 않는 잘못 설계된 API를 처리하는 데 유용할 수 있습니다.

```julia
function qsort(a::Vector{T}, cmp) where T
    isbits(T) || throw(ArgumentError("this method can only qsort isbits arrays"))
    callback = @cfunction $cmp Cint (Ref{T}, Ref{T})
    # Here, `callback` isa Base.CFunction, which will be converted to Ptr{Cvoid}
    # (and protected against finalization) by the ccall
    @ccall qsort(a::Ptr{T}, length(a)::Csize_t, Base.elsize(a)::Csize_t, callback::Ptr{Cvoid})
    # We could instead use:
    #    GC.@preserve callback begin
    #        use(Base.unsafe_convert(Ptr{Cvoid}, callback))
    #    end
    # if we needed to use it outside of a `ccall`
    return a
end
```

!!! note
    Closure [`@cfunction`](@ref)는 모든 플랫폼에서 사용할 수 없는 LLVM 트램폴린에 의존합니다(예: ARM 및 PowerPC).


## Closing a Library

때때로 라이브러리를 닫고(언로드) 다시 로드하는 것이 유용할 수 있습니다. 예를 들어, Julia와 함께 사용할 C 코드를 개발할 때, C 코드를 컴파일하고 Julia에서 호출한 다음, 라이브러리를 닫고, 수정한 후, 다시 컴파일하고 새로운 변경 사항을 로드해야 할 수 있습니다. Julia를 다시 시작하거나 `Libdl` 함수를 사용하여 라이브러리를 명시적으로 관리할 수 있습니다.

```julia
lib = Libdl.dlopen("./my_lib.so") # Open the library explicitly.
sym = Libdl.dlsym(lib, :my_fcn)   # Get a symbol for the function to call.
@ccall $sym(...) # Use the pointer `sym` instead of the library.symbol tuple.
Libdl.dlclose(lib) # Close the library explicitly.
```

`@ccall`을 사용할 때 입력(예: `@ccall "./my_lib.so".my_fcn(...)::Cvoid`)에 유의하세요. 라이브러리는 암묵적으로 열리며 명시적으로 닫히지 않을 수 있습니다.

## Variadic function calls

가변 인자를 갖는 C 함수를 호출할 때, `세미콜론`을 사용하여 필수 인자와 가변 인자를 구분할 수 있습니다. 아래는 `printf` 함수의 예입니다:

```julia-repl
julia> @ccall printf("%s = %d\n"::Cstring ; "foo"::Cstring, foo::Cint)::Cint
foo = 3
8
```

## [`ccall` interface](@id ccall-interface)

`@ccall`에 대한 또 다른 대체 인터페이스가 있습니다. 이 인터페이스는 약간 덜 편리하지만 [calling convention](@ref calling-convention)을 지정할 수 있습니다.

[`ccall`](@ref)에 대한 인자는:

1. A `(:function, "library")` 쌍 (가장 일반적임),

    또는

    `:function` 이름 기호 또는 `"function"` 이름 문자열 (현재 프로세스 또는 libc의 기호에 대해),

    또는

    함수 포인터(예: `dlsym`에서).
2. 함수의 반환 유형
3. 함수 시그니처에 해당하는 입력 유형의 튜플입니다. 일반적인 실수 중 하나는 인수 유형의 1-튜플이 후행 쉼표와 함께 작성되어야 한다는 것을 잊는 것입니다.
4. 함수에 전달될 실제 인수 값, 있는 경우; 각각은 별도의 매개변수입니다.

!!! note
    `(:function, "library")` 쌍, 반환 유형 및 입력 유형은 리터럴 상수여야 합니다 (즉, 변수일 수 없지만 [Non-constant Function Specifications](@ref)를 참조하십시오).

    나머지 매개변수는 포함된 메서드가 정의될 때 컴파일 타임에 평가됩니다.


아래에 매크로와 함수 인터페이스 간의 번역 표가 제공됩니다.

|                                                                     `@ccall` |                                                                     `ccall` |
| ----------------------------------------------------------------------------:| ---------------------------------------------------------------------------:|
|                                                      `@ccall clock()::Int32` |                                                  `ccall(:clock, Int32, ())` |
|                                                    `@ccall f(a::Cint)::Cint` |                                               `ccall(:a, Cint, (Cint,), a)` |
|                               `@ccall "mylib".f(a::Cint, b::Cdouble)::Cvoid` |                      `ccall((:f, "mylib"), Cvoid, (Cint, Cdouble), (a, b))` |
|                                                    `@ccall $fptr.f()::Cvoid` |                                                 `ccall(fptr, f, Cvoid, ())` |
|      `@ccall printf("%s = %d\n"::Cstring ; "foo"::Cstring, foo::Cint)::Cint` |                                                             `<unavailable>` |
| `@ccall printf("%s = %s\n"::Cstring ; "2 + 2"::Cstring, "5"::Cstring)::Cint` |    `ccall(:printf, Cint, (Cstring, Cstring...), "%s = %s\n", "2 + 2", "5")` |
|                                                              `<unavailable>` | `ccall(:gethostname, stdcall, Int32, (Ptr{UInt8}, UInt32), hn, length(hn))` |

## [Calling Convention](@id calling-convention)

`ccall`의 두 번째 인수(반환 유형 바로 앞)는 선택적으로 호출 규칙 지정자일 수 있습니다(`@ccall` 매크로는 현재 호출 규칙을 지정하는 것을 지원하지 않습니다). 지정자가 없으면 플랫폼 기본 C 호출 규칙이 사용됩니다. 지원되는 다른 규칙은 `stdcall`, `cdecl`, `fastcall`, 및 `thiscall`입니다(64비트 Windows에서는 효과가 없습니다). 예를 들어(`base/libc.jl`에서) 위와 동일한 `gethostname``ccall`을 볼 수 있지만 Windows에 대한 올바른 서명이 있습니다:

```julia
hn = Vector{UInt8}(undef, 256)
err = ccall(:gethostname, stdcall, Int32, (Ptr{UInt8}, UInt32), hn, length(hn))
```

자세한 내용은 [LLVM Language Reference](https://llvm.org/docs/LangRef.html#calling-conventions)를 참조하십시오.

추가적인 특별 호출 규약 [`llvmcall`](@ref Base.llvmcall)가 있으며, 이는 LLVM 내장 함수를 직접 호출할 수 있도록 허용합니다. 이는 GPGPU와 같은 특이한 플랫폼을 대상으로 할 때 특히 유용할 수 있습니다. 예를 들어, [CUDA](https://llvm.org/docs/NVPTXUsage.html)의 경우, 스레드 인덱스를 읽을 수 있어야 합니다:

```julia
ccall("llvm.nvvm.read.ptx.sreg.tid.x", llvmcall, Int32, ())
```

`ccall`과 마찬가지로, 인수 서명을 정확하게 맞추는 것이 필수적입니다. 또한, `Core.Intrinsics`에 의해 노출된 동등한 Julia 함수와 달리, 내재 함수가 현재 대상에서 의미가 있고 작동하도록 보장하는 호환성 계층이 없다는 점에 유의해야 합니다.

## Accessing Global Variables

네이티브 라이브러리에서 내보낸 전역 변수는 [`cglobal`](@ref) 함수를 사용하여 이름으로 접근할 수 있습니다. `4d61726b646f776e2e436f64652822222c202263676c6f62616c2229_40726566`의 인자는 [`ccall`](@ref)에서 사용되는 기호 사양과 동일하며, 변수에 저장된 값을 설명하는 유형입니다:

```julia-repl
julia> cglobal((:errno, :libc), Int32)
Ptr{Int32} @0x00007f418d0816b8
```

결과는 값의 주소를 제공하는 포인터입니다. 이 포인터를 통해 [`unsafe_load`](@ref) 및 [`unsafe_store!`](@ref)를 사용하여 값을 조작할 수 있습니다.

!!! note
    이 `errno` 기호는 "libc"라는 라이브러리에서 찾을 수 없을 수 있으며, 이는 시스템 컴파일러의 구현 세부 사항입니다. 일반적으로 표준 라이브러리 기호는 이름으로만 접근해야 하며, 컴파일러가 올바른 기호를 채워 넣을 수 있도록 해야 합니다. 그러나 이 예제에서 보여지는 `errno` 기호는 대부분의 컴파일러에서 특별하며, 따라서 여기서 보이는 값은 아마도 당신이 기대하거나 원하는 값이 아닐 것입니다. 멀티 스레드 기능을 지원하는 시스템에서 C로 동등한 코드를 컴파일하면 일반적으로 다른 함수를 호출하게 되며(매크로 전처리기 오버로딩을 통해), 여기서 인쇄된 레거시 값과는 다른 결과를 제공할 수 있습니다.


## Accessing Data through a Pointer

다음 방법들은 "안전하지 않다"고 설명되며, 잘못된 포인터나 타입 선언이 줄리아를 갑자기 종료시킬 수 있습니다.

주어진 `Ptr{T}`에 대해, 타입 `T`의 내용은 일반적으로 `unsafe_load(ptr, [index])`를 사용하여 참조된 메모리에서 줄리아 객체로 복사할 수 있습니다. 인덱스 인자는 선택 사항이며(기본값은 1), 줄리아 관례에 따라 1 기반 인덱싱을 따릅니다. 이 함수는 의도적으로 [`getindex`](@ref) 및 [`setindex!`](@ref)의 동작과 유사합니다(예: `[]` 접근 구문).

반환 값은 참조된 메모리의 내용을 복사하여 포함하도록 초기화된 새로운 객체가 됩니다. 참조된 메모리는 안전하게 해제하거나 릴리스할 수 있습니다.

`T`가 `Any`인 경우, 메모리는 Julia 객체에 대한 참조(`jl_value_t*`)를 포함하고 있는 것으로 가정되며, 결과는 이 객체에 대한 참조가 되고 객체는 복사되지 않습니다. 이 경우 객체가 항상 가비지 컬렉터에 보이도록 해야 하며(포인터는 포함되지 않지만 새로운 참조는 포함됩니다) 메모리가 조기에 해제되지 않도록 주의해야 합니다. 객체가 원래 Julia에 의해 할당되지 않은 경우, 새로운 객체는 절대 Julia의 가비지 컬렉터에 의해 최종화되지 않습니다. `Ptr` 자체가 실제로 `jl_value_t*`인 경우, [`unsafe_pointer_to_objref(ptr)`](@ref)를 사용하여 다시 Julia 객체 참조로 변환할 수 있습니다. (Julia 값 `v`는 [`pointer_from_objref(v)`](@ref)를 호출하여 `Ptr{Cvoid}` 포인터로 변환할 수 있습니다.)

역방향 작업(`Ptr{T}`에 데이터 쓰기)은 [`unsafe_store!(ptr, value, [index])`](@ref)를 사용하여 수행할 수 있습니다. 현재 이는 원시 타입 또는 다른 포인터가 없는(`isbits`) 불변 구조체 타입에 대해서만 지원됩니다.

오류를 발생시키는 모든 작업은 현재 구현되지 않았을 가능성이 높으며, 해결될 수 있도록 버그로 게시해야 합니다.

관심 있는 포인터가 일반 데이터 배열(원시 유형 또는 불변 구조체)인 경우, 함수 [`unsafe_wrap(Array, ptr,dims, own = false)`](@ref)가 더 유용할 수 있습니다. 마지막 매개변수는 Julia가 기본 버퍼의 "소유권을 가져가고" 반환된 `Array` 객체가 최종화될 때 `free(ptr)`를 호출해야 하는 경우 true여야 합니다. `own` 매개변수가 생략되거나 false인 경우, 호출자는 모든 접근이 완료될 때까지 버퍼가 존재하도록 보장해야 합니다.

Julia의 `Ptr` 타입에서의 산술 연산(예: `+` 사용)은 C의 포인터 산술과 동일하게 작동하지 않습니다. Julia에서 `Ptr`에 정수를 더하면 항상 포인터가 *바이트* 단위로 이동하며, 요소 단위로 이동하지 않습니다. 이렇게 하면 포인터 산술에서 얻은 주소 값은 포인터의 요소 타입에 의존하지 않습니다.

## Thread-safety

일부 C 라이브러리는 다른 스레드에서 콜백을 실행하며, Julia는 스레드 안전하지 않기 때문에 추가적인 주의가 필요합니다. 특히, 두 계층 시스템을 설정해야 합니다: C 콜백은 "실제" 콜백의 실행을 *예약*해야 합니다(줄리아의 이벤트 루프를 통해). 이를 위해 [`AsyncCondition`](@ref Base.AsyncCondition) 객체를 생성하고 그 위에서 [`wait`](@ref)를 호출하세요:

```julia
cond = Base.AsyncCondition()
wait(cond)
```

C에 전달하는 콜백은 [`ccall`](@ref)를 `:uv_async_send`에 실행해야 하며, 인수로 `cond.handle`을 전달해야 하며, Julia 런타임과의 할당이나 다른 상호작용을 피해야 합니다.

이벤트가 병합될 수 있으므로, `uv_async_send`에 대한 여러 호출이 조건에 대한 단일 깨움 알림으로 이어질 수 있음을 유의하십시오.

## More About Callbacks

C 라이브러리에 콜백을 전달하는 방법에 대한 자세한 내용은 이 링크를 참조하세요: [blog post](https://julialang.org/blog/2013/05/callback).

## C++

C++ 바인딩을 생성하기 위한 도구는 [CxxWrap](https://github.com/JuliaInterop/CxxWrap.jl) 패키지를 참조하세요.

[^1]: Non-library function calls in both C and Julia can be inlined and thus may have even less overhead than calls to shared library functions. The point above is that the cost of actually doing foreign function call is about the same as doing a call in either native language.

[^2]: The [Clang package](https://github.com/ihnorton/Clang.jl) can be used to auto-generate Julia code from a C header file.
