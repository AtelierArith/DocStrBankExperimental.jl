# [Modules](@id modules)

모듈은 Julia에서 코드를 일관된 단위로 조직하는 데 도움을 줍니다. 모듈은 `module NameOfModule ... end` 구문으로 구분되며, 다음과 같은 특징이 있습니다:

1. 모듈은 각각 새로운 전역 범위를 도입하는 별도의 네임스페이스입니다. 이는 유용한데, 서로 다른 함수나 전역 변수가 충돌 없이 같은 이름을 사용할 수 있게 해주기 때문입니다. 단, 이들은 별도의 모듈에 있어야 합니다.
2. 모듈은 상세한 네임스페이스 관리를 위한 기능을 제공합니다: 각 모듈은 `export`하여 `public`으로 표시하는 이름 집합을 정의하고, `using` 및 `import`를 통해 다른 모듈에서 이름을 가져올 수 있습니다(아래에서 설명합니다).
3. 모듈은 더 빠른 로딩을 위해 미리 컴파일될 수 있으며, 런타임 초기화를 위한 코드를 포함할 수 있습니다.

일반적으로, 더 큰 Julia 패키지에서는 모듈 코드가 파일로 조직되어 있는 것을 볼 수 있습니다. 예를 들어,

```julia
module SomeModule

# export, public, using, import statements are usually here; we discuss these below

include("file1.jl")
include("file2.jl")

end
```

파일과 파일 이름은 대부분 모듈과 관련이 없으며, 모듈은 오직 모듈 표현식과만 관련이 있습니다. 모듈당 여러 파일을 가질 수 있으며, 파일당 여러 모듈을 가질 수 있습니다. `include`는 소스 파일의 내용이 포함하는 모듈의 전역 범위에서 평가되는 것처럼 동작합니다. 이 장에서는 짧고 간단한 예제를 사용하므로 `include`를 사용하지 않을 것입니다.

모듈 본문을 들여쓰지 않는 것이 권장되는 스타일입니다. 이는 일반적으로 전체 파일이 들여쓰기 되기 때문입니다. 또한 모듈 이름에는 `UpperCamelCase`를 사용하는 것이 일반적이며(타입과 마찬가지로), 모듈에 유사한 이름의 식별자가 포함된 경우에는 이름 충돌을 피하기 위해 복수형을 사용하는 것이 좋습니다. 예를 들어,

```julia
module FastThings

struct FastThing
    ...
end

end
```

## [Namespace management](@id namespace-management)

네임스페이스 관리는 모듈의 이름을 다른 모듈에서 사용할 수 있도록 하는 언어가 제공하는 기능을 의미합니다. 관련 개념과 기능에 대해 아래에서 자세히 논의합니다.

### Qualified names

전역 범위의 함수, 변수 및 유형의 이름은 `sin`, `ARGS`, `UnitRange`와 같이 항상 *부모 모듈*에 속하며, 이는 [`parentmodule`](@ref)를 사용하여 대화형으로 찾을 수 있습니다.

```jldoctest
julia> parentmodule(UnitRange)
Base
```

이름은 부모 모듈을 접두사로 붙여 `Base.UnitRange`와 같이 외부에서 참조할 수 있습니다. 이를 *자격 이름*이라고 합니다. 부모 모듈은 `Base.Math.sin`과 같이 하위 모듈 체인을 사용하여 접근할 수 있으며, 여기서 `Base.Math`는 *모듈 경로*라고 합니다. 구문적 모호성으로 인해 연산자와 같은 기호만 포함된 이름을 자격을 부여하려면 콜론을 삽입해야 하며, 예를 들어 `Base.:+`와 같습니다. 소수의 연산자는 추가로 괄호가 필요합니다. 예를 들어 `Base.:(==)`와 같습니다.

이름이 자격이 있다면, 항상 *접근 가능*하며, 함수의 경우 자격 있는 이름을 함수 이름으로 사용하여 메서드를 추가할 수도 있습니다.

모듈 내에서 변수 이름은 `global x`로 선언함으로써 할당하지 않고도 "예약"될 수 있습니다. 이는 로드 시간 이후에 초기화된 전역 변수에 대한 이름 충돌을 방지합니다. 구문 `M.x = y`는 다른 모듈에서 전역 변수를 할당하는 데 작동하지 않으며, 전역 할당은 항상 모듈 로컬입니다.

### Export lists

이름(함수, 타입, 전역 변수 및 상수를 지칭)은 `export`를 사용하여 모듈의 *내보내기 목록*에 추가할 수 있습니다. 이는 모듈을 `using`할 때 가져오는 기호입니다. 일반적으로 소스 코드의 독자가 쉽게 찾을 수 있도록 모듈 정의의 맨 위 또는 그 근처에 위치합니다.

```jldoctest module_manual
julia> module NiceStuff
       export nice, DOG
       struct Dog end      # singleton type, not exported
       const DOG = Dog()   # named instance, exported
       nice(x) = "nice $x" # function, exported
       end;

```

하지만 이것은 단지 스타일 제안일 뿐입니다 — 모듈은 임의의 위치에 여러 개의 `export` 문을 가질 수 있습니다.

API(응용 프로그래밍 인터페이스)의 일부를 형성하는 이름을 내보내는 것은 일반적입니다. 위 코드에서 내보내기 목록은 사용자가 `nice`와 `DOG`를 사용해야 함을 제안합니다. 그러나 자격이 있는 이름은 항상 식별자를 접근 가능하게 만들기 때문에, 이는 API를 구성하는 옵션일 뿐입니다: 다른 언어와 달리 Julia는 모듈 내부를 진정으로 숨기는 기능이 없습니다.

또한, 일부 모듈은 이름을 전혀 내보내지 않습니다. 이는 일반적으로 `derivative`와 같은 일반적인 단어를 API에서 사용할 경우 다른 모듈의 내보내기 목록과 쉽게 충돌할 수 있기 때문에 이루어집니다. 이름 충돌을 관리하는 방법은 아래에서 살펴보겠습니다.

이름을 `using NiceStuff`를 호출하는 사람들의 네임스페이스로 내보내지 않고 공개로 표시하려면 `export` 대신 `public`을 사용할 수 있습니다. 이렇게 하면 공개 이름이 공개 API의 일부로 표시되지만 네임스페이스에는 영향을 미치지 않습니다. `public` 키워드는 Julia 1.11 이상에서만 사용할 수 있습니다. Julia 1.10 및 이전 버전과의 호환성을 유지하려면 [Compat](https://github.com/JuliaLang/Compat.jl) 패키지의 `@compat` 매크로를 사용하세요.

### Standalone `using` and `import`

대화형 사용을 위해 모듈을 로드하는 가장 일반적인 방법은 `using ModuleName`입니다. 이 [loads](@ref code-loading)는 `ModuleName`과 관련된 코드를 가져옵니다.

1. 모듈 이름
2. 및 내보내기 목록의 요소를 주변 전역 네임스페이스로.

기술적으로, `using ModuleName` 문장은 `ModuleName`이라는 모듈이 필요에 따라 이름을 해결하는 데 사용 가능하다는 것을 의미합니다. 현재 모듈에서 정의되지 않은 전역 변수가 발견되면, 시스템은 `ModuleName`에서 내보낸 변수들 중에서 이를 검색하고, 거기에서 발견되면 이를 사용합니다. 이는 현재 모듈 내에서 그 전역 변수를 사용하는 모든 경우가 `ModuleName`에서 해당 변수의 정의로 해결된다는 것을 의미합니다.

패키지에서 모듈을 로드하려면 `using ModuleName` 문을 사용할 수 있습니다. 로컬로 정의된 모듈에서 모듈을 로드하려면 모듈 이름 앞에 점을 추가해야 합니다. 예: `using .ModuleName`.

예를 들어 계속하자면,

```jldoctest module_manual
julia> using .NiceStuff
```

위 코드를 로드하면 `NiceStuff`(모듈 이름), `DOG` 및 `nice`가 사용 가능해집니다. `Dog`는 내보내기 목록에 없지만, 모듈 경로(여기서는 모듈 이름인 `NiceStuff`로만 표시됨)를 사용하여 이름을 지정하면 접근할 수 있습니다. 즉, `NiceStuff.Dog`로 접근할 수 있습니다.

중요하게도, **`using ModuleName`은 export 목록이 전혀 중요한 유일한 형태입니다**.

대조적으로,

```jldoctest module_manual
julia> import .NiceStuff
```

모듈 이름만 범위로 가져옵니다. 사용자는 `NiceStuff.DOG`, `NiceStuff.Dog`, 및 `NiceStuff.nice`를 사용하여 그 내용을 접근해야 합니다. 일반적으로 `import ModuleName`은 사용자가 네임스페이스를 깔끔하게 유지하고 싶을 때 사용됩니다. 다음 섹션에서 볼 수 있듯이 `import .NiceStuff`는 `using .NiceStuff: NiceStuff`와 동일합니다.

여러 개의 `using` 및 `import` 문을 같은 종류로 쉼표로 구분된 표현식으로 결합할 수 있습니다. 예:

```jldoctest module_manual
julia> using LinearAlgebra, Random
```

### `using` and `import` with specific identifiers, and adding methods

`using ModuleName:` 또는 `import ModuleName:` 다음에 쉼표로 구분된 이름 목록이 오면, 모듈이 로드되지만 *오직 그 특정 이름들만이 해당 문장에 의해 네임스페이스로 가져옵니다.* 예를 들어,

```jldoctest module_manual
julia> using .NiceStuff: nice, DOG
```

`nice`와 `DOG`라는 이름을 가져올 것입니다.

중요하게도, 모듈 이름 `NiceStuff`는 *네임스페이스*에 포함되지 않습니다. 이를 접근 가능하게 만들고 싶다면, 명시적으로 나열해야 합니다.

```jldoctest module_manual
julia> using .NiceStuff: nice, DOG, NiceStuff
```

두 개 이상의 패키지/모듈이 이름을 내보내고 그 이름이 각 패키지에서 동일한 것을 참조하지 않을 때, 그리고 패키지가 명시적인 이름 목록 없이 `using`을 통해 로드될 때, 자격 없이 해당 이름을 참조하는 것은 오류입니다. 따라서 향후 버전의 종속성과 Julia와의 호환성을 염두에 두고 작성된 코드, 예를 들어 릴리스된 패키지의 코드는 각 로드된 패키지에서 사용하는 이름을 나열하는 것이 권장됩니다. 예를 들어 `using Foo: Foo, f`와 같이 사용하는 것이 좋으며, `using Foo`와 같이 사용하는 것은 피해야 합니다.

줄리아는 겉보기에는 같은 것에 대해 두 가지 형태를 가지고 있습니다. 왜냐하면 `import ModuleName: f`만이 모듈 경로 없이 `f`에 메서드를 추가할 수 있게 해주기 때문입니다. 즉, 다음 예제는 오류를 발생시킬 것입니다:

```jldoctest module_manual
julia> using .NiceStuff: nice

julia> struct Cat end

julia> nice(::Cat) = "nice 😸"
ERROR: invalid method definition in Main: function NiceStuff.nice must be explicitly imported to be extended
Stacktrace:
 [1] top-level scope
   @ none:0
 [2] top-level scope
   @ none:1

```

이 오류는 의도한 대로만 사용하려는 다른 모듈의 함수에 메서드를 실수로 추가하는 것을 방지합니다.

이 문제를 처리하는 두 가지 방법이 있습니다. 항상 모듈 경로로 함수 이름을 한정할 수 있습니다:

```jldoctest module_manual
julia> using .NiceStuff

julia> struct Cat end

julia> NiceStuff.nice(::Cat) = "nice 😸"

```

대신, 특정 함수 이름을 `import`할 수 있습니다:

```jldoctest module_manual
julia> import .NiceStuff: nice

julia> struct Cat end

julia> nice(::Cat) = "nice 😸"
nice (generic function with 2 methods)
```

어떤 것을 선택하느냐는 스타일의 문제입니다. 첫 번째 형식은 다른 모듈의 함수에 메서드를 추가하고 있다는 것을 분명히 해줍니다(임포트와 메서드 정의가 별도의 파일에 있을 수 있다는 점을 기억하세요). 반면 두 번째 형식은 더 짧아서 여러 메서드를 정의할 때 특히 편리합니다.

변수가 `using` 또는 `import`를 통해 가시화되면, 모듈은 동일한 이름의 변수를 생성할 수 없습니다. 가져온 변수는 읽기 전용이며, 전역 변수에 할당하면 항상 현재 모듈이 소유한 변수에 영향을 미치거나 오류를 발생시킵니다.

### Renaming with `as`

`import` 또는 `using`으로 범위에 도입된 식별자는 `as` 키워드를 사용하여 이름을 변경할 수 있습니다. 이는 이름 충돌을 피하거나 이름을 줄이는 데 유용합니다. 예를 들어, `Base`는 함수 이름 `read`를 내보내지만, CSV.jl 패키지도 `CSV.read`를 제공합니다. CSV 읽기를 여러 번 호출할 예정이라면 `CSV.` 한정자를 생략하는 것이 편리할 것입니다. 그러나 그러면 `Base.read`를 참조하는지 `CSV.read`를 참조하는지 모호해집니다:

```julia-repl
julia> read;

julia> import CSV: read
WARNING: ignoring conflicting import of CSV.read into Main
```

이름 변경은 해결책을 제공합니다:

```julia-repl
julia> import CSV: read as rd
```

가져온 패키지 자체도 이름을 변경할 수 있습니다:

```julia
import BenchmarkTools as BT
```

`as`는 단일 식별자가 범위에 도입될 때만 `using`과 함께 작동합니다. 예를 들어 `using CSV: read as rd`는 작동하지만, `using CSV as C`는 작동하지 않습니다. 이는 `CSV`의 모든 내보낸 이름에 대해 작동하기 때문입니다.

### Mixing multiple `using` and `import` statements

여러 개의 `using` 또는 `import` 문이 위의 형태 중 하나로 사용될 때, 그 효과는 나타나는 순서에 따라 결합됩니다. 예를 들어,

```jldoctest module_manual
julia> using .NiceStuff         # exported names and the module name

julia> import .NiceStuff: nice  # allows adding methods to unqualified functions

```

`NiceStuff`의 모든 내보낸 이름과 모듈 이름 자체를 범위로 가져오고, 또한 `nice`에 모듈 이름을 접두사로 붙이지 않고도 메서드를 추가할 수 있게 합니다.

### Handling name conflicts

두 개 이상의 패키지가 동일한 이름을 내보내는 상황을 고려해 보십시오.

```jldoctest module_manual
julia> module A
       export f
       f() = 1
       end
A
julia> module B
       export f
       f() = 2
       end
B
```

`using .A, .B`는 작동하지만 `f`를 호출하려고 하면 오류가 발생하고 힌트가 제공됩니다.

```jldoctest module_manual
julia> using .A, .B

julia> f
ERROR: UndefVarError: `f` not defined in `Main`
Hint: It looks like two or more modules export different bindings with this name, resulting in ambiguity. Try explicitly importing it from a particular module, or qualifying the name with the module it should come from.
```

여기서 줄리아는 당신이 어떤 `f`를 언급하고 있는지 결정할 수 없으므로, 선택을 해야 합니다. 다음 솔루션은 일반적으로 사용됩니다:

1. 간단히 `A.f` 및 `B.f`와 같은 자격 있는 이름을 사용하세요. 이렇게 하면 코드의 독자에게 맥락이 명확해지며, 특히 `f`가 우연히 일치하지만 다양한 패키지에서 다른 의미를 가질 경우 더욱 그렇습니다. 예를 들어, `degree`는 수학, 자연 과학 및 일상 생활에서 다양한 용도로 사용되며, 이러한 의미는 구분되어야 합니다.
2. `as` 키워드를 사용하여 하나 또는 두 개의 식별자를 이름을 바꿉니다. 예:

    ```jldoctest module_manual
    julia> using .A: f as f

    julia> using .B: f as g

    ```

    `B.f`를 `g`로 사용할 수 있게 합니다. 여기서 우리는 `using A`를 사용하지 않았다고 가정하고 있으며, 이는 `f`를 네임스페이스로 가져왔을 것입니다.
3. 문제가 되는 이름들이 *의미*를 공유할 때, 한 모듈이 다른 모듈에서 이를 가져오거나, 다른 패키지에서 사용할 수 있는 인터페이스를 정의하는 유사한 기능만을 가진 경량 “기본” 패키지를 갖는 것이 일반적입니다. 이러한 패키지 이름은 `...Base`로 끝나는 것이 관례입니다(이는 Julia의 `Base` 모듈과는 아무 관련이 없습니다).

### Default top-level definitions and bare modules

모듈은 자동으로 `using Core`, `using Base`를 포함하고, [`eval`](@ref) 및 [`include`](@ref) 함수의 정의를 포함합니다. 이 함수들은 해당 모듈의 전역 범위 내에서 표현식/파일을 평가합니다.

이 기본 정의가 원하지 않는 경우, 모듈은 키워드 [`baremodule`](@ref)를 사용하여 정의할 수 있습니다 (참고: `Core`는 여전히 가져옵니다). `baremodule` 측면에서 표준 `module`은 다음과 같이 보입니다:

```
baremodule Mod

using Base

eval(x) = Core.eval(Mod, x)
include(p) = Base.include(Mod, p)

...

end
```

만약 `Core`조차 원하지 않는다면, 아무것도 가져오지 않고 이름을 전혀 정의하지 않는 모듈을 `Module(:YourNameHere, false, false)`로 정의할 수 있으며, 코드는 [`@eval`](@ref) 또는 [`Core.eval`](@ref)를 사용하여 그 안에 평가될 수 있습니다:

```jldoctest
julia> arithmetic = Module(:arithmetic, false, false)
Main.arithmetic

julia> @eval arithmetic add(x, y) = $(+)(x, y)
add (generic function with 1 method)

julia> arithmetic.add(12, 13)
25
```

### Standard modules

중요한 표준 모듈이 세 가지 있습니다:

  * [`Core`](@ref)는 언어에 "내장된" 모든 기능을 포함합니다.
  * [`Base`](@ref)는 거의 모든 경우에 유용한 기본 기능을 포함하고 있습니다.
  * [`Main`](@ref)는 Julia가 시작될 때의 최상위 모듈이자 현재 모듈입니다.

!!! note "Standard library modules"
    기본적으로 Julia는 몇 가지 표준 라이브러리 모듈을 함께 제공합니다. 이들은 일반 Julia 패키지처럼 작동하지만, 명시적으로 설치할 필요는 없습니다. 예를 들어, 단위 테스트를 수행하고 싶다면 다음과 같이 `Test` 표준 라이브러리를 로드할 수 있습니다:

    ```julia
    using Test
    ```


## Submodules and relative paths

모듈은 *서브모듈*을 포함할 수 있으며, 같은 구문 `module ... end`을 중첩할 수 있습니다. 이는 복잡한 코드베이스를 조직하는 데 유용한 별도의 네임스페이스를 도입하는 데 사용될 수 있습니다. 각 `module`은 고유한 [scope](@ref scope-of-variables)을 도입하므로, 서브모듈은 부모로부터 이름을 자동으로 “상속”하지 않습니다.

하위 모듈은 `using` 및 `import` 문에서 *상대 모듈 한정자*를 사용하여 포함된 상위 모듈(후자를 포함하여) 내의 다른 모듈을 참조하는 것이 권장됩니다. 상대 모듈 한정자는 현재 모듈에 해당하는 마침표(`.`)로 시작하며, 각 연속적인 `.`는 현재 모듈의 상위 모듈로 이어집니다. 필요에 따라 모듈이 뒤따를 수 있으며, 결국 접근할 실제 이름이 `.`로 구분되어 나열됩니다.

다음 예를 고려해 보세요. 여기서 서브모듈 `SubA`는 함수를 정의하고, 그 후 "형제" 모듈에서 확장됩니다:

```jldoctest module_manual
julia> module ParentModule
       module SubA
       export add_D  # exported interface
       const D = 3
       add_D(x) = x + D
       end
       using .SubA  # brings `add_D` into the namespace
       export add_D # export it from ParentModule too
       module SubB
       import ..SubA: add_D # relative path for a “sibling” module
       struct Infinity end
       add_D(x::Infinity) = x
       end
       end;

```

패키지에서 코드를 볼 수 있으며, 유사한 상황에서 사용됩니다.

```jldoctest module_manual
julia> import .ParentModule.SubA: add_D

```

그러나 이것은 [code loading](@ref code-loading)를 통해 작동하므로 `ParentModule`이 패키지에 있을 때만 작동합니다. 상대 경로를 사용하는 것이 더 좋습니다.

정의의 순서도 값 평가 시 중요하다는 점에 유의하세요. 고려해 보세요.

```julia
module TestPackage

export x, y

x = 0

module Sub
using ..TestPackage
z = y # ERROR: UndefVarError: `y` not defined in `Main`
end

y = 1

end
```

`Sub`는 `TestPackage.y`가 정의되기 전에 사용하려고 하므로 값이 없습니다.

유사한 이유로, 순환 순서를 사용할 수 없습니다:

```julia
module A

module B
using ..C # ERROR: UndefVarError: `C` not defined in `Main.A`
end

module C
using ..B
end

end
```

## Module initialization and precompilation

대형 모듈은 모듈의 모든 문장을 실행하는 데 종종 많은 양의 코드를 컴파일해야 하므로 로드하는 데 몇 초가 걸릴 수 있습니다. Julia는 이 시간을 줄이기 위해 모듈의 미리 컴파일된 캐시를 생성합니다.

미리 컴파일된 모듈 파일(때때로 "캐시 파일"이라고도 함)은 `import` 또는 `using`이 모듈을 로드할 때 자동으로 생성되고 사용됩니다. 캐시 파일이 아직 존재하지 않으면 모듈이 컴파일되어 향후 재사용을 위해 저장됩니다. 또한 [`Base.compilecache(Base.identify_package("modulename"))`](@ref)를 수동으로 호출하여 모듈을 로드하지 않고도 이러한 파일을 생성할 수 있습니다. 생성된 캐시 파일은 `DEPOT_PATH[1]`의 `compiled` 하위 폴더에 저장됩니다. 시스템에 대한 변경 사항이 없다면, 이러한 캐시 파일은 `import` 또는 `using`으로 모듈을 로드할 때 사용됩니다.

프리컴파일 캐시 파일은 모듈, 타입, 메서드 및 상수의 정의를 저장합니다. 또한 메서드 특수화 및 이를 위해 생성된 코드를 저장할 수 있지만, 이는 일반적으로 개발자가 명시적인 [`precompile`](@ref) 지시어를 추가하거나 패키지 빌드 중에 컴파일을 강제하는 작업을 실행해야 합니다.

그러나 모듈의 종속성을 업데이트하거나 소스 코드를 변경하면 `using` 또는 `import` 시 모듈이 자동으로 다시 컴파일됩니다. 종속성은 모듈이 가져오는 모듈, 줄리아 빌드, 포함된 파일 또는 모듈 파일에서 [`include_dependency(path)`](@ref)에 의해 선언된 명시적 종속성입니다.

파일 종속성이 `include`에 의해 로드될 때, 변경 사항은 파일 크기(`fsize`) 또는 내용(해시로 압축된)을 검사하여 결정됩니다. `include_dependency`에 의해 로드된 파일 종속성의 경우, 변경 사항은 수정 시간(`mtime`)이 변경되지 않았는지 또는 수정 시간이 초 단위로 잘린 것과 같은지를 검사하여 결정됩니다(서브 초 정확도로 mtime을 복사할 수 없는 시스템을 고려하기 위해). 또한 `require`의 검색 로직에 의해 선택된 파일 경로가 사전 컴파일 파일을 생성한 경로와 일치하는지 여부도 고려합니다. 현재 프로세스에 이미 로드된 종속성 집합도 고려하며, 파일이 변경되거나 사라지더라도 이러한 모듈을 다시 컴파일하지 않아서 실행 중인 시스템과 사전 컴파일 캐시 간의 불일치를 피합니다. 마지막으로, [compile-time preferences](@ref preferences)의 변경 사항도 고려합니다.

모듈이 *사전 컴파일*에 안전하지 않다는 것을 알고 있다면 (예를 들어, 아래 설명된 이유 중 하나로 인해), 모듈 파일에 `__precompile__(false)`를 넣어야 합니다 (일반적으로 파일 상단에 배치). 이렇게 하면 `Base.compilecache`가 오류를 발생시키고, `using` / `import`가 이를 현재 프로세스에 직접 로드하여 사전 컴파일 및 캐싱을 건너뛰게 됩니다. 이로 인해 해당 모듈이 다른 사전 컴파일된 모듈에 의해 가져오는 것을 방지합니다.

특정 행동이 점진적 공유 라이브러리 생성에 내재되어 있음을 인식할 필요가 있을 수 있으며, 이는 모듈을 작성할 때 주의가 필요할 수 있습니다. 예를 들어, 외부 상태는 유지되지 않습니다. 이를 수용하기 위해, *런타임*에서 발생해야 하는 초기화 단계와 *컴파일 타임*에 발생할 수 있는 단계를 명시적으로 분리하십시오. 이 목적을 위해, Julia는 모듈 내에서 런타임에서 발생해야 하는 초기화 단계를 실행하는 `__init__()` 함수를 정의할 수 있도록 허용합니다. 이 함수는 컴파일 중(`--output-*`)에 호출되지 않습니다. 효과적으로, 이 함수는 코드의 생애 동안 정확히 한 번 실행될 것이라고 가정할 수 있습니다. 물론 필요하다면 수동으로 호출할 수 있지만, 기본적으로 이 함수는 로컬 머신의 상태를 계산하는 데 관련된 것으로 가정되며, 이는 컴파일된 이미지에 캡처될 필요가 없거나 심지어 캡처되어서는 안 됩니다. 이 함수는 모듈이 프로세스에 로드된 후에 호출되며, 점진적 컴파일(`--output-incremental=yes`)로 로드되는 경우에도 포함되지만, 전체 컴파일 프로세스에 로드되는 경우에는 호출되지 않습니다.

특히, 모듈에서 `function __init__()`을 정의하면, Julia는 모듈이 로드된 직후(예: `import`, `using`, 또는 `require`에 의해) 런타임에서 *처음*으로 `__init__()`을 호출합니다(즉, `__init__`은 한 번만 호출되며, 모듈 내의 모든 문장이 실행된 후에만 호출됩니다). 모듈이 완전히 가져온 후에 호출되기 때문에, 모든 하위 모듈이나 다른 가져온 모듈의 `__init__` 함수는 포함된 모듈의 `__init__`보다 *먼저* 호출됩니다.

`__init__`의 두 가지 전형적인 용도는 외부 C 라이브러리의 런타임 초기화 함수를 호출하고 외부 라이브러리에서 반환된 포인터와 관련된 전역 상수를 초기화하는 것입니다. 예를 들어, 런타임에 `foo_init()` 초기화 함수를 호출해야 하는 C 라이브러리 `libfoo`를 호출한다고 가정해 보겠습니다. 또한 `libfoo`에 정의된 `void *foo_data()` 함수의 반환 값을 보유하는 전역 상수 `foo_data_ptr`를 정의하고 싶다고 가정해 보겠습니다. 이 상수는 포인터 주소가 실행마다 변경되기 때문에 런타임에 초기화되어야 합니다(컴파일 타임이 아님). 모듈에 다음 `__init__` 함수를 정의하여 이를 수행할 수 있습니다:

```julia
const foo_data_ptr = Ref{Ptr{Cvoid}}(0)
function __init__()
    ccall((:foo_init, :libfoo), Cvoid, ())
    foo_data_ptr[] = ccall((:foo_data, :libfoo), Ptr{Cvoid}, ())
    nothing
end
```

함수 `__init__` 내에서 전역 변수를 정의하는 것이 완벽하게 가능하다는 점에 유의하십시오. 이것은 동적 언어를 사용하는 장점 중 하나입니다. 그러나 이를 전역 범위에서 상수로 만들면 컴파일러가 타입을 알 수 있도록 하여 더 최적화된 코드를 생성할 수 있습니다. 명백히, `foo_data_ptr`에 의존하는 모듈의 다른 전역 변수들도 `__init__`에서 초기화되어야 합니다.

[`ccall`](@ref)에 의해 생성되지 않은 대부분의 Julia 객체와 관련된 상수는 `__init__`에 배치할 필요가 없습니다: 그 정의는 미리 컴파일되고 캐시된 모듈 이미지에서 로드될 수 있습니다. 여기에는 배열과 같은 복잡한 힙 할당 객체가 포함됩니다. 그러나 원시 포인터 값을 반환하는 모든 루틴은 미리 컴파일이 작동하기 위해 런타임에 호출되어야 합니다 ([`Ptr`](@ref) 객체는 [`isbits`](@ref) 객체 안에 숨겨지지 않는 한 null 포인터로 변환됩니다). 여기에는 Julia 함수 [`@cfunction`](@ref) 및 [`pointer`](@ref)의 반환 값이 포함됩니다.

사전 및 집합 유형, 또는 일반적으로 `hash(key)` 메서드의 출력에 의존하는 모든 것은 더 복잡한 경우입니다. 키가 숫자, 문자열, 기호, 범위, `Expr` 또는 이러한 유형의 조합(배열, 튜플, 집합, 쌍 등을 통해)인 일반적인 경우에는 미리 컴파일하는 것이 안전합니다. 그러나 `Function` 또는 `DataType`과 같은 몇 가지 다른 키 유형이나 `hash` 메서드를 정의하지 않은 일반 사용자 정의 유형의 경우, 기본 `hash` 메서드는 객체의 메모리 주소(그 객체의 `objectid`를 통해)에 의존하므로 실행할 때마다 변경될 수 있습니다. 이러한 키 유형 중 하나가 있거나 확실하지 않은 경우, 안전하게 하려면 `__init__` 함수 내에서 이 사전을 초기화할 수 있습니다. 또는 컴파일 타임에 안전하게 초기화되도록 특별히 처리된 [`IdDict`](@ref) 사전 유형을 사용할 수 있습니다.

사전 컴파일을 사용할 때는 컴파일 단계와 실행 단계 간의 구분을 명확히 하는 것이 중요합니다. 이 모드에서는 줄리아가 임의의 줄리아 코드를 실행할 수 있는 컴파일러이지, 컴파일된 코드를 생성하는 독립 실행형 인터프리터가 아님이 훨씬 더 명확하게 드러납니다.

다른 알려진 잠재적 실패 시나리오에는 다음이 포함됩니다:

1. 전역 카운터(예: 객체를 고유하게 식별하기 위한 시도). 다음 코드 스니펫을 고려하십시오:

    ```julia
    mutable struct UniquedById
        myid::Int
        let counter = 0
            UniquedById() = new(counter += 1)
        end
    end
    ```

    이 코드의 의도는 모든 인스턴스에 고유한 ID를 부여하는 것이었지만, 카운터 값은 컴파일이 끝날 때 기록됩니다. 이후 이 점진적으로 컴파일된 모듈의 모든 사용은 동일한 카운터 값에서 시작됩니다.

    `objectid`(메모리 포인터를 해싱하여 작동하는)는 유사한 문제를 가지고 있음을 유의하십시오(아래 `Dict` 사용에 대한 노트 참조).

    한 가지 대안은 매크로를 사용하여 [`@__MODULE__`](@ref)를 캡처하고 현재 `counter` 값과 함께 별도로 저장하는 것이지만, 이 전역 상태에 의존하지 않도록 코드를 재설계하는 것이 더 나을 수 있습니다.
2. 연관 컬렉션(예: `Dict` 및 `Set`)은 `__init__`에서 재해시가 필요합니다. (앞으로 초기화 함수 등록을 위한 메커니즘이 제공될 수 있습니다.)
3. 로드 타임을 통해 지속되는 컴파일 타임 부작용에 따라 다릅니다. 예를 들면: 다른 줄리아 모듈에서 배열이나 다른 변수를 수정하기; 열린 파일이나 장치에 대한 핸들을 유지하기; 다른 시스템 리소스(메모리 포함)에 대한 포인터를 저장하기;
4. 전역 범위에서 다른 모듈의 전역 상태를 직접 참조하여 우연히 "복사본"을 생성하는 것. 예를 들어:

    ```julia
    #mystdout = Base.stdout #= will not work correctly, since this will copy Base.stdout into this module =#
    # instead use accessor functions:
    getstdout() = Base.stdout #= best option =#
    # or move the assignment into the runtime:
    __init__() = global mystdout = Base.stdout #= also works =#
    ```

코드를 미리 컴파일하는 동안 사용자가 다른 잘못된 동작 상황을 피할 수 있도록 추가적인 제한이 여러 가지 적용됩니다:

1. [`eval`](@ref)를 호출하여 다른 모듈에서 부작용을 발생시킵니다. 이는 증분 사전 컴파일 플래그가 설정되어 있을 때 경고가 발생하게 됩니다.
2. `__init__()`가 시작된 후 로컬 범위에서 `global const` 문을 사용할 수 없습니다 (이와 관련된 오류 추가 계획은 이슈 #12010을 참조하세요).
3. 모듈을 교체하는 것은 증분 사전 컴파일을 수행하는 동안 런타임 오류입니다.

알아두어야 할 몇 가지 다른 사항:

1. 소스 파일 자체에 변경이 이루어진 후(예: `Pkg.update`에 의해) 코드 리로드/캐시 무효화가 수행되지 않으며, `Pkg.rm` 후에 정리 작업이 수행되지 않습니다.
2. 재구성된 배열의 메모리 공유 동작은 사전 컴파일에 의해 무시됩니다(각 뷰는 자체 복사본을 가집니다).
3. 파일 시스템이 컴파일 타임과 런타임 사이에 변경되지 않을 것으로 기대합니다. 예를 들어, [`@__FILE__`](@ref)/`source_path()`를 사용하여 런타임에 리소스를 찾거나 BinDeps `@checked_lib` 매크로를 사용할 수 있습니다. 때때로 이것은 피할 수 없습니다. 그러나 가능할 때는 런타임에 찾을 필요가 없도록 리소스를 컴파일 타임에 모듈로 복사하는 것이 좋은 관행이 될 수 있습니다.
4. `WeakRef` 객체와 파이널라이저는 현재 직렬 변환기에서 제대로 처리되지 않습니다(이는 곧 출시될 버전에서 수정될 예정입니다).
5. 내부 메타데이터 객체의 인스턴스에 대한 참조를 캡처하는 것은 일반적으로 피하는 것이 가장 좋습니다. 예를 들어 `Method`, `MethodInstance`, `MethodTable`, `TypeMapLevel`, `TypeMapEntry` 및 이러한 객체의 필드와 같은 것들이 있습니다. 이는 직렬 변환기를 혼란스럽게 할 수 있으며 원하는 결과를 얻지 못할 수 있습니다. 이렇게 하는 것이 반드시 오류는 아니지만, 시스템이 이러한 것들 중 일부를 복사하고 다른 것들의 단일 고유 인스턴스를 생성하려고 시도할 것에 대비해야 합니다.

모듈 개발 중에는 점진적 사전 컴파일을 끄는 것이 도움이 될 때가 있습니다. 명령줄 플래그 `--compiled-modules={yes|no|existing}`를 사용하면 모듈 사전 컴파일을 켜고 끌 수 있습니다. `--compiled-modules=no`로 Julia를 시작하면 컴파일 캐시의 직렬화된 모듈이 모듈 및 모듈 의존성을 로드할 때 무시됩니다. 경우에 따라 기존의 사전 컴파일된 모듈을 로드하고 싶지만 새로운 모듈을 생성하고 싶지 않을 수 있습니다. 이는 `--compiled-modules=existing`로 Julia를 시작하여 수행할 수 있습니다. `--pkgimages={yes|no|existing}`를 사용하면 사전 컴파일 중 네이티브 코드 저장소에만 영향을 미치는 보다 세밀한 제어가 가능합니다. `Base.compilecache`는 여전히 수동으로 호출할 수 있습니다. 이 명령줄 플래그의 상태는 `Pkg.build`에 전달되어 패키지를 설치, 업데이트 및 명시적으로 빌드할 때 자동 사전 컴파일 트리거를 비활성화합니다.

환경 변수를 사용하여 일부 전처리 실패를 디버깅할 수도 있습니다. `JULIA_VERBOSE_LINKING=true`를 설정하면 컴파일된 네이티브 코드의 공유 라이브러리 링크 실패를 해결하는 데 도움이 될 수 있습니다. Julia 매뉴얼의 **개발자 문서** 부분을 참조하면 "패키지 이미지" 아래의 Julia 내부 문서화 섹션에서 추가 세부정보를 찾을 수 있습니다.
