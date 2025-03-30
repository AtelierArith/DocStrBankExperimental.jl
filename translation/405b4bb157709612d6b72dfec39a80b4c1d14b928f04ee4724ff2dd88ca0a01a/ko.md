# Julia ASTs

줄리아는 코드의 두 가지 표현을 가지고 있습니다. 첫 번째는 파서에 의해 반환된 표면 구문 AST입니다(예: [`Meta.parse`](@ref) 함수)이며, 매크로에 의해 조작됩니다. 이는 문자 스트림에서 `julia-parser.scm`에 의해 구성된 코드의 구조화된 표현입니다. 다음으로는 낮은 형태, 즉 IR(중간 표현)이 있습니다. 이는 타입 추론 및 코드 생성에 사용됩니다. 낮은 형태에서는 노드의 유형이 더 적고, 모든 매크로가 확장되며, 모든 제어 흐름이 명시적 분기 및 문장 시퀀스로 변환됩니다. 낮은 형태는 `julia-syntax.scm`에 의해 구성됩니다.

먼저 우리는 매크로를 작성하는 데 필요한 AST에 집중할 것입니다.

## Surface syntax AST

프론트 엔드 AST는 거의 전적으로 [`Expr`](@ref)와 원자(예: 기호, 숫자)로 구성됩니다. 일반적으로 각 시각적으로 구별되는 구문 형식에 대해 다른 표현 헤드가 있습니다. 예시는 s-표현식 구문으로 제공됩니다. 각 괄호로 묶인 목록은 Expr에 해당하며, 첫 번째 요소는 헤드입니다. 예를 들어 `(call f x)`는 Julia에서 `Expr(:call, :f, :x)`에 해당합니다.

### Calls

| Input            | AST                                |
|:---------------- |:---------------------------------- |
| `f(x)`           | `(call f x)`                       |
| `f(x, y=1, z=2)` | `(call f x (kw y 1) (kw z 2))`     |
| `f(x; y=1)`      | `(call f (parameters (kw y 1)) x)` |
| `f(x...)`        | `(call f (... x))`                 |

`do` 구문:

```julia
f(x) do a,b
    body
end
```

`(do (call f x) (-> (tuple a b) (block body)))`로 파싱됩니다.

### Operators

대부분의 연산자 사용은 단순한 함수 호출이므로 `call` 헤드로 파싱됩니다. 그러나 일부 연산자는 특별한 형태(반드시 함수 호출은 아님)이며, 이러한 경우 연산자 자체가 표현식 헤드입니다. julia-parser.scm에서는 이를 "구문 연산자"라고 합니다. 일부 연산자(`+` 및 `*`)는 N-항 파싱을 사용하며, 체인 호출은 단일 N-인수 호출로 파싱됩니다. 마지막으로, 비교 체인은 고유한 특별한 표현식 구조를 가지고 있습니다.

| Input       | AST                       |
|:----------- |:------------------------- |
| `x+y`       | `(call + x y)`            |
| `a+b+c+d`   | `(call + a b c d)`        |
| `2x`        | `(call * 2 x)`            |
| `a&&b`      | `(&& a b)`                |
| `x += 1`    | `(+= x 1)`                |
| `a ? 1 : 2` | `(if a 1 2)`              |
| `a,b`       | `(tuple a b)`             |
| `a==b`      | `(call == a b)`           |
| `1<i<=n`    | `(comparison 1 < i <= n)` |
| `a.b`       | `(. a (quote b))`         |
| `a.(b)`     | `(. a (tuple b))`         |

### Bracketed forms

| Input                    | AST                                             |
|:------------------------ |:----------------------------------------------- |
| `a[i]`                   | `(ref a i)`                                     |
| `t[i;j]`                 | `(typed_vcat t i j)`                            |
| `t[i j]`                 | `(typed_hcat t i j)`                            |
| `t[a b; c d]`            | `(typed_vcat t (row a b) (row c d))`            |
| `t[a b;;; c d]`          | `(typed_ncat t 3 (row a b) (row c d))`          |
| `a{b}`                   | `(curly a b)`                                   |
| `a{b;c}`                 | `(curly a (parameters c) b)`                    |
| `[x]`                    | `(vect x)`                                      |
| `[x,y]`                  | `(vect x y)`                                    |
| `[x;y]`                  | `(vcat x y)`                                    |
| `[x y]`                  | `(hcat x y)`                                    |
| `[x y; z t]`             | `(vcat (row x y) (row z t))`                    |
| `[x;y;; z;t;;;]`         | `(ncat 3 (nrow 2 (nrow 1 x y) (nrow 1 z t)))`   |
| `[x for y in z, a in b]` | `(comprehension (generator x (= y z) (= a b)))` |
| `T[x for y in z]`        | `(typed_comprehension T (generator x (= y z)))` |
| `(a, b, c)`              | `(tuple a b c)`                                 |
| `(a; b; c)`              | `(block a b c)`                                 |

### Macros

| Input         | AST                                          |
|:------------- |:-------------------------------------------- |
| `@m x y`      | `(macrocall @m (line) x y)`                  |
| `Base.@m x y` | `(macrocall (. Base (quote @m)) (line) x y)` |
| `@Base.m x y` | `(macrocall (. Base (quote @m)) (line) x y)` |

### Strings

| Input           | AST                                 |
|:--------------- |:----------------------------------- |
| `"a"`           | `"a"`                               |
| `x"y"`          | `(macrocall @x_str (line) "y")`     |
| `x"y"z`         | `(macrocall @x_str (line) "y" "z")` |
| `"x = $x"`      | `(string "x = " x)`                 |
| ``` `a b c` ``` | `(macrocall @cmd (line) "a b c")`   |

문서 문자열 구문:

```julia
"some docs"
f(x) = x
```

파싱 결과는 `(macrocall (|.| Core '@doc) (line) "some docs" (= (call f x) (block x)))`입니다.

### Imports and such

| Input               | AST                                 |
|:------------------- |:----------------------------------- |
| `import a`          | `(import (. a))`                    |
| `import a.b.c`      | `(import (. a b c))`                |
| `import ...a`       | `(import (. . . . a))`              |
| `import a.b, c.d`   | `(import (. a b) (. c d))`          |
| `import Base: x`    | `(import (: (. Base) (. x)))`       |
| `import Base: x, y` | `(import (: (. Base) (. x) (. y)))` |
| `export a, b`       | `(export a b)`                      |

`using`는 `import`와 동일한 표현을 가지지만, 표현 머리 부분이 `:using` 대신 `:import`입니다.

### Numbers

줄리아는 많은 스킴 구현보다 더 많은 숫자 유형을 지원하므로, 모든 숫자가 AST에서 스킴 숫자로 직접 표현되지는 않습니다.

| Input                   | AST                                                      |
|:----------------------- |:-------------------------------------------------------- |
| `11111111111111111111`  | `(macrocall @int128_str nothing "11111111111111111111")` |
| `0xfffffffffffffffff`   | `(macrocall @uint128_str nothing "0xfffffffffffffffff")` |
| `1111...many digits...` | `(macrocall @big_str nothing "1111....")`                |

### Block forms

블록 문은 `(block stmt1 stmt2 ...)`로 구문 분석됩니다.

If 문:

```julia
if a
    b
elseif c
    d
else
    e
end
```

파싱됨:

```
(if a (block (line 2) b)
    (elseif (block (line 3) c) (block (line 4) d)
            (block (line 6 e))))
```

`while` 루프는 `(while 조건 본문)`으로 구문 분석됩니다.

`for` 루프는 `(for (= var iter) body)`로 구문 분석됩니다. 반복 사양이 하나 이상인 경우, 이들은 블록으로 구문 분석됩니다: `(for (block (= v1 iter1) (= v2 iter2)) body)`입니다.

`break`와 `continue`는 0-인자 표현식 `(break)`와 `(continue)`로 파싱됩니다.

`let`는 `(let (= var val) body)` 또는 `(let (block (= var1 val1) (= var2 val2) ...) body)`로 파싱됩니다. 이는 `for` 루프와 유사합니다.

기본 함수 정의는 `(function (call f x) body)`로 구문 분석됩니다. 더 복잡한 예:

```julia
function f(x::T; k = 1) where T
    return x+1
end
```

파싱됨:

```
(function (where (call f (parameters (kw k 1))
                       (:: x T))
                 T)
          (block (line 2) (return (call + x 1))))
```

타입 정의:

```julia
mutable struct Foo{T<:S}
    x::T
end
```

파싱됨:

```
(struct true (curly Foo (<: T S))
        (block (line 2) (:: x T)))
```

첫 번째 인자는 해당 타입이 변경 가능한지 여부를 나타내는 불리언입니다.

`try` 블록은 `(try try_block var catch_block finally_block)`으로 파싱됩니다. `catch` 뒤에 변수가 없으면 `var`는 `#f`입니다. `finally` 절이 없으면 마지막 인자는 존재하지 않습니다.

### Quote expressions

줄리아 소스 구문 형식은 코드 인용(`quote` 및 `:( )`)에 대해 `$`를 사용한 보간을 지원합니다. Lisp 용어로, 이는 실제로 "백쿼트" 또는 "준쿼트" 형식이라는 것을 의미합니다. 내부적으로는 보간 없이 코드 인용이 필요합니다. 줄리아의 스킴 코드에서 비보간 인용은 표현식 헤드 `inert`로 나타납니다.

`inert` 표현식은 Julia `QuoteNode` 객체로 변환됩니다. 이 객체는 모든 유형의 단일 값을 감싸며, 평가될 때 단순히 해당 값을 반환합니다.

원자(atom)를 인자로 가진 `quote` 표현식은 `QuoteNode`로 변환됩니다.

### Line numbers

소스 위치 정보는 `(line line_num file_name)` 형식으로 표현되며, 세 번째 구성 요소는 선택 사항입니다(현재 줄 번호가 변경되지만 파일 이름은 변경되지 않을 때 생략됨).

이 표현식은 Julia에서 `LineNumberNode`로 표현됩니다.

### Macros

매크로 위생은 `escape`와 `hygienic-scope`라는 헤드 쌍을 통해 표현됩니다. 매크로 확장의 결과는 자동으로 `(hygienic-scope block module)`로 감싸져 새로운 범위의 결과를 나타냅니다. 사용자는 호출자에서 코드를 보간하기 위해 내부에 `(escape block)`을 삽입할 수 있습니다.

## Lowered form

하향식 표현(IR)은 컴파일러에 더 중요합니다. 이는 타입 추론, 인라인과 같은 최적화 및 코드 생성에 사용되기 때문입니다. 또한 입력 구문에서 상당한 재배치의 결과로 나타나기 때문에 인간에게는 덜 명확합니다.

`Symbol` 및 일부 숫자 유형 외에도, 다음 데이터 유형이 축소된 형태로 존재합니다:

  * `Expr`

    `head` 필드로 표시된 노드 유형이 있으며, `args` 필드는 하위 표현식의 `Vector{Any}`입니다. 표면 AST의 거의 모든 부분이 `Expr`로 표현되는 반면, IR은 주로 호출 및 일부 최상위 전용 형식에 대해 제한된 수의 `Expr`만 사용합니다.
  * `슬롯번호`

    인수와 지역 변수를 연속 번호로 식별합니다. 슬롯 인덱스를 제공하는 정수 값의 `id` 필드가 있습니다. 이러한 슬롯의 유형은 해당 `CodeInfo` 객체의 `slottypes` 필드에서 찾을 수 있습니다.
  * `주장`

    `SlotNumber`와 동일하지만 최적화 후에만 나타납니다. 참조된 슬롯이 포함된 함수의 인수임을 나타냅니다.
  * `코드정보`

    일련의 문장의 IR을 감쌉니다. `code` 필드는 실행할 표현식의 배열입니다.
  * `GotoNode`

    무조건 분기. 인자는 점프할 코드 배열의 인덱스로 표현된 분기 대상입니다.
  * `GotoIfNot`

    조건 분기. `cond` 필드가 false로 평가되면, `dest` 필드에 의해 식별된 인덱스로 이동합니다.
  * `ReturnNode`

    인수(`val` 필드)를 포함하는 함수의 값으로 반환합니다. 만약 `val` 필드가 정의되지 않은 경우, 이는 도달할 수 없는 문장을 나타냅니다.
  * `QuoteNode`

    임의의 값을 데이터로 참조하기 위해 래핑합니다. 예를 들어, 함수 `f() = :a`는 `value` 필드가 기호 `a`인 `QuoteNode`를 포함하여 기호 자체를 평가하는 대신 반환합니다.
  * `GlobalRef`

    모듈 `mod`의 전역 변수 `name`을 참조합니다.
  * `SSAValue`

    연속적으로 번호가 매겨진(1부터 시작) 정적 단일 할당(SSA) 변수를 컴파일러가 삽입한 것을 나타냅니다. `SSAValue`의 번호(`id`)는 그것이 나타내는 표현식의 값의 코드 배열 인덱스입니다.
  * `NewvarNode`

    변수가 생성되는 지점을 표시합니다(슬롯). 이로 인해 변수가 정의되지 않은 상태로 초기화됩니다.

### `Expr` types

이 기호들은 [`Expr`](@ref)의 `head` 필드에 소문자로 나타납니다.

  * `전화`

    함수 호출(동적 디스패치). `args[1]`는 호출할 함수이고, `args[2:end]`는 인수입니다.
  * `호출`

    함수 호출 (정적 디스패치). `args[1]`는 호출할 MethodInstance이며, `args[2:end]`는 인수입니다 (여기에는 호출되고 있는 함수가 `args[2]`에 포함됩니다).
  * `정적_매개변수`

    정적 매개변수를 인덱스로 참조합니다.
  * `=`

    과제. IR에서 첫 번째 인자는 항상 `SlotNumber` 또는 `GlobalRef`입니다.
  * `방법`

    제네릭 함수에 메서드를 추가하고 필요할 경우 결과를 할당합니다.

    1-인수 형태와 3-인수 형태가 있습니다. 1-인수 형태는 `function foo end` 구문에서 발생합니다. 1-인수 형태에서 인수는 기호입니다. 이 기호가 현재 범위에서 이미 함수의 이름인 경우 아무 일도 일어나지 않습니다. 기호가 정의되지 않은 경우, 새로운 함수가 생성되어 기호로 지정된 식별자에 할당됩니다. 기호가 정의되어 있지만 비함수를 이름짓는 경우, 오류가 발생합니다. "함수를 이름짓는다"는 정의는 바인딩이 상수이며, 단일 객체 유형의 객체를 참조한다는 것입니다. 이는 단일 객체 유형의 인스턴스가 메서드를 추가할 유형을 고유하게 식별하기 때문입니다. 유형에 필드가 있을 경우, 메서드가 인스턴스에 추가되는 것인지 그 유형에 추가되는 것인지 명확하지 않습니다.

    3-인수 형식은 다음과 같은 인수를 가집니다:

      * `args[1]`

        함수 이름, 또는 알 수 없거나 필요하지 않은 경우 `nothing`. 기호인 경우, 표현식은 먼저 위의 1-인수 형태처럼 동작합니다. 이 인수는 그 이후로 무시됩니다. 메서드가 엄격히 타입에 의해 추가될 때 `nothing`일 수 있으며, `(::T)(x) = x` 또는 기존 함수에 메서드가 추가될 때 `MyModule.f(x) = x`일 수 있습니다.
      * `args[2]`

        `SimpleVector`의 인수 유형 데이터. `args[2][1]`은 인수 유형의 `SimpleVector`이며, `args[2][2]`는 메서드의 정적 매개변수에 해당하는 유형 변수의 `SimpleVector`입니다.
      * `args[3]`

        메서드 자체의 `CodeInfo`. "범위를 벗어난" 메서드 정의(다른 범위에 정의된 메서드도 있는 함수에 메서드를 추가하는 경우)에 대해, 이는 `:lambda` 표현식으로 평가되는 표현식입니다.
  * `구조체_유형`

    7개의 인수를 사용하는 새로운 `struct`를 정의하는 표현식:

      * `args[1]`

        `struct`의 이름
      * `args[2]`

        `SimpleVector`의 매개변수를 지정하는 `call` 표현식
      * `args[3]`

        `fieldnames`를 지정하여 `SimpleVector`를 생성하는 `call` 표현식
      * `args[4]`

        `Symbol`, `GlobalRef` 또는 `Expr`는 수퍼타입을 지정합니다 (예: `:Integer`, `GlobalRef(Core, :Any)` 또는 `:(Core.apply_type(AbstractArray, T, N))`)
      * `args[5]`

        `SimpleVector`의 필드 타입을 지정하는 `call` 표현식
      * `args[6]`

        A Bool, true if `mutable`
      * `args[7]`

        초기화할 인수의 수입니다. 이는 필드의 수 또는 내부 생성자의 `new` 문에 의해 호출되는 최소 필드 수가 될 것입니다.
  * `추상_유형`

    3개의 인수를 가진 표현식으로 새로운 추상 유형을 정의합니다. 인수는 `struct_type` 표현식의 인수 1, 2 및 4와 동일합니다.
  * `원시_타입`

    4개의 인수를 가진 표현식으로 새로운 원시 타입을 정의합니다. 인수 1, 2 및 4는 `struct_type`과 동일합니다. 인수 3은 비트 수입니다.

    !!! compat "Julia 1.5"
        `struct_type`, `abstract_type`, `primitive_type`는 Julia 1.5에서 제거되었고 새로운 내장 함수 호출로 대체되었습니다.
  * `글로벌`

    전역 바인딩을 선언합니다.
  * `const`

    전역 변수를 상수로 선언합니다.
  * `새로운`

    새로운 구조체와 유사한 객체를 할당합니다. 첫 번째 인자는 타입입니다. [`new`](@ref) 의사 함수는 이것으로 축소되며, 타입은 항상 컴파일러에 의해 삽입됩니다. 이는 매우 내부 전용 기능이며, 어떤 검사도 수행하지 않습니다. 임의의 `new` 표현식을 평가하면 쉽게 세그멘테이션 오류가 발생할 수 있습니다.
  * `splatnew`

    `new`와 유사하지만, 필드 값이 단일 튜플로 전달됩니다. `new`가 일급 함수라면 `splat(new)`와 유사하게 작동하므로 이러한 이름이 붙었습니다.
  * `isdefined`

    `Expr(:isdefined, :x)`는 현재 범위에서 `x`가 이미 정의되었는지를 나타내는 Bool을 반환합니다.
  * `the_exception`

    `catch` 블록 내에서 포착된 예외를 반환하며, 이는 `jl_current_exception(ct)`에 의해 반환됩니다.
  * `입력`

    예외 처리기를 입력합니다(`setjmp`). `args[1]`는 오류 발생 시 점프할 catch 블록의 레이블입니다. `pop_exception`에 의해 소비되는 토큰을 생성합니다.
  * `휴가`

    예외 처리기를 팝합니다. `args[1]`는 팝할 처리기 수입니다.
  * `pop_exception`

    catch 블록을 나갈 때 현재 예외의 스택을 관련된 `enter` 상태로 되돌립니다. `args[1]`에는 관련된 `enter`의 토큰이 포함되어 있습니다.

    !!! compat "Julia 1.1"
        `pop_exception`은 Julia 1.1에서 새로 추가되었습니다.
  * `인바운드`

    경계 검사 켜기 또는 끄기 제어. 스택이 유지되며, 이 표현식의 첫 번째 인수가 true 또는 false인 경우(`true`는 경계 검사가 비활성화됨), 스택에 푸시됩니다. 첫 번째 인수가 `:pop`인 경우, 스택에서 팝됩니다.
  * `boundscheck`

    `@inbounds`가 표시된 코드 섹션에 인라인되면 `false` 값을 가지며, 그렇지 않으면 `true` 값을 가집니다.
  * `루프정보`

    루프의 끝을 표시합니다. `LowerSimdLoop`에 전달되는 메타데이터를 포함하여 `@simd` 표현식의 내부 루프를 표시하거나 LLVM 루프 패스에 정보를 전파합니다.
  * `copyast`

    부분적으로 준 인용의 구현입니다. 인자는 단순히 재귀적으로 복사되어 런타임에 반환되는 표면 구문 AST입니다.
  * `메타`

    메타데이터. `args[1]`은 일반적으로 메타데이터의 종류를 지정하는 기호이며, 나머지 인수는 자유 형식입니다. 다음은 일반적으로 사용되는 메타데이터의 종류입니다:

      * `:inline` 및 `:noinline`: 인라인 힌트.
  * `foreigncall`

    정적으로 계산된 `ccall` 정보용 컨테이너. 필드는:

      * `args[1]` : 이름

        외부 함수에 대해 구문 분석될 표현식.
      * `args[2]::Type` : RT

        포함된 메서드가 정의될 때 정적으로 계산된 (리터럴) 반환 유형.
      * `args[3]::SimpleVector` (of Types) : AT

        포함된 메서드가 정의될 때 정적으로 계산된 인수 유형의 (리터럴) 벡터.
      * `args[4]::Int` : nreq

        가변 인수 함수 정의에 필요한 인수의 수.
      * `args[5]::QuoteNode{Symbol}` : 호출 규약

        호출을 위한 호출 규약.
      * `args[6:5+length(args[3])]` : 인수

        모든 인수의 값(각 인수의 유형은 args[3]에 제공됨).
      * `args[6+length(args[3])+1:end]` : gc-루트

        호출 기간 동안 gc-rooted 되어야 할 추가 객체입니다. 이러한 객체가 어디에서 유래되었고 어떻게 처리되는지에 대한 내용은 [Working with LLVM](@ref Working-with-LLVM)를 참조하십시오.
  * `new_opaque_closure`

    새로운 불투명 클로저를 생성합니다. 필드는 다음과 같습니다:

      * `args[1]` : 서명

        불투명 클로저의 함수 시그니처. 불투명 클로저는 디스패치에 참여하지 않지만, 입력 타입은 제한될 수 있습니다.
      * `args[2]` : isva

        클로저가 가변 인자를 허용하는지 여부를 나타냅니다.
      * `args[3]` : lb

        출력 유형에 대한 하한. (기본값은 `Union{}`)
      * `args[4]` : ub

        출력 유형에 대한 상한. (기본값은 `Any`)
      * `args[5]` : 메서드

        `opaque_closure_method` 표현으로서의 실제 메서드.
      * `args[6:end]` : 캡처

        불투명 클로저에 의해 캡처된 값들.

    !!! compat "Julia 1.7"
        불투명 클로저는 Julia 1.7에 추가되었습니다.

### [Method](@id ast-lowered-method)

단일 메서드에 대한 공유 메타데이터를 설명하는 고유한 컨테이너.

  * `이름`, `모듈`, `파일`, `라인`, `시그`

    메타데이터는 컴퓨터와 인간을 위해 방법을 고유하게 식별합니다.
  * `모호한`

    이 방법과 모호할 수 있는 다른 방법의 캐시.
  * `전문 분야`

    이 메서드에 대해 생성된 모든 MethodInstance의 캐시로, 고유성을 보장하는 데 사용됩니다. 고유성은 효율성을 위해 필요하며, 특히 점진적 사전 컴파일 및 메서드 무효화 추적에 중요합니다.
  * `소스`

    원본 소스 코드(사용 가능한 경우, 일반적으로 압축됨).
  * `발전기`

    특정 메서드 시그니처에 대한 특화된 소스를 얻기 위해 실행할 수 있는 호출 가능한 객체입니다.
  * `뿌리`

    AST에 압축, 타입 추론 또는 네이티브 코드 생성을 위해 인터폴레이션된 비AST 항목에 대한 포인터.
  * `nargs`, `isva`, `called`, `is_for_opaque_closure`,

    이 메서드의 소스 코드에 대한 설명적인 비트 필드.
  * `기본_세계`

    이 방법을 "소유"하는 세계 시대.

### MethodInstance

고유한 컨테이너로, 메서드에 대한 단일 호출 가능한 서명을 설명합니다. 특히 [Proper maintenance and care of multi-threading locks](@ref Proper-maintenance-and-care-of-multi-threading-locks)를 참조하여 이러한 필드를 안전하게 수정하는 방법에 대한 중요한 세부정보를 확인하십시오.

  * `specTypes`

    이 MethodInstance의 기본 키입니다. 고유성은 `def.specializations` 조회를 통해 보장됩니다.
  * `def`

    이 함수가 설명하는 `Method`의 특수화입니다. 또는 `Module`입니다. 이는 모듈에서 확장된 최상위 Lambda이며, Method의 일부가 아닙니다.
  * `sparam_vals`

    `specTypes`의 정적 매개변수 값입니다. `Method.unspecialized`의 `MethodInstance`에 대해, 이는 빈 `SimpleVector`입니다. 그러나 `MethodTable` 캐시에서 가져온 런타임 `MethodInstance`의 경우, 이는 항상 정의되어 있으며 인덱스할 수 있습니다.
  * `추론되지 않음`

    최상위 thunk에 대한 압축되지 않은 소스 코드. 또한, 생성된 함수의 경우, 소스 코드를 찾을 수 있는 여러 장소 중 하나입니다.
  * `백엣지`

    우리는 새로운 메서드 정의 후에 필요할 수 있는 점진적 재분석/재컴파일 작업을 효율적으로 추적하기 위해 캐시 종속성의 역 목록을 저장합니다. 이는 이 `MethodInstance`에 대한 가능한 호출을 포함하도록 추론되거나 최적화된 다른 `MethodInstance`의 목록을 유지함으로써 작동합니다. 이러한 최적화 결과는 `cache`의 어딘가에 저장되었을 수 있으며, 상수 전파와 같이 우리가 캐시하고 싶지 않았던 결과일 수도 있습니다. 따라서 우리는 여기에서 다양한 캐시 항목에 대한 모든 백엣지를 병합합니다(어쨌든 최대 세계에 대한 센티넬 값이 있는 적용 가능한 캐시 항목은 거의 항상 하나뿐입니다).
  * `캐시`

    이 템플릿 인스턴스를 공유하는 `CodeInstance` 객체의 캐시입니다.

### CodeInstance

  * `def`

    이 캐시 항목이 파생된 `MethodInstance`.
  * `소유자`

    이 `CodeInstance`의 소유자를 나타내는 토큰입니다. 일치시키기 위해 `jl_egal`을 사용할 것입니다.

  * `rettype`/`rettype_const`

    `specFunctionObject` 필드에 대한 추론된 반환 유형은 일반적으로 함수의 계산된 반환 유형이기도 합니다.
  * `추론된`

    이 함수의 추론된 소스에 대한 캐시를 포함할 수 있으며, `rettype`이 추론되었음을 나타내기 위해 `nothing`으로 설정될 수도 있습니다.
  * `ftpr`

    일반적인 jlcall 진입점.
  * `jlcall_api`

    `fptr`를 호출할 때 사용할 ABI. 몇 가지 중요한 것들은 다음과 같습니다:

      * 0 - 아직 컴파일되지 않음
      * 1 - `JL_CALLABLE` `jl_value_t *(*)(jl_function_t *f, jl_value_t *args[nargs], uint32_t nargs)`
      * 2 - 상수 (값이 `rettype_const`에 저장됨)
      * 3 - 정적 매개변수가 전달된 `jl_value_t *(*)(jl_svec_t *sparams, jl_function_t *f, jl_value_t *args[nargs], uint32_t nargs)`
      * 4 - 인터프리터에서 실행 `jl_value_t *(*)(jl_method_instance_t *meth, jl_function_t *f, jl_value_t *args[nargs], uint32_t nargs)`
  * `min_world` / `max_world`

    이 메서드 인스턴스를 호출하는 데 유효한 세계 연령의 범위입니다. 만약 max_world가 특별한 토큰 값 `-1`이라면, 그 값은 아직 알려지지 않았습니다. 우리는 다시 고려해야 하는 백엣지를 만날 때까지 계속 사용할 수 있습니다.

### CodeInfo

소스 코드를 보관하기 위한 (일반적으로 임시) 컨테이너입니다.

  * `코드`

    `Any` 배열의 문장
  * `슬롯이름`

    슬롯(인수 또는 지역 변수)마다 이름을 부여하는 기호 배열.
  * `슬롯플래그`

    슬롯 속성을 비트 플래그로 나타낸 `UInt8` 배열:

      * 0x02 - 할당됨 (이 변수의 왼쪽에 할당문이 *없*을 경우에만 거짓)
      * 0x08 - 사용됨 (슬롯에 대한 읽기 또는 쓰기가 있는 경우)
      * 0x10 - 정적으로 한 번 할당됨
      * 0x20 - 할당되기 전에 사용될 수 있습니다. 이 플래그는 타입 추론 후에만 유효합니다.
  * `ssavaluetypes`

    배열 또는 `Int`입니다.

    `Int`인 경우, 함수 내에서 컴파일러가 삽입한 임시 위치의 수(즉, `code` 배열의 길이)를 제공합니다. 배열인 경우, 각 위치에 대한 유형을 지정합니다.
  * `ssaflags`

    함수의 각 표현식에 대한 문장 수준 32비트 플래그. 자세한 내용은 julia.h의 `jl_code_info_t` 정의를 참조하십시오.
  * `linetable`

    소스 위치 객체의 배열
  * `codelocs`

    정수 인덱스 배열로, 각 문장과 관련된 위치를 `linetable`에서 제공합니다.

선택적 필드:

  * `슬롯타입`

    슬롯에 대한 타입 배열.
  * `rettype`

    하향식 형태(IR)의 추론된 반환 유형. 기본값은 `Any`입니다.
  * `추론_제한_휴리스틱을_위한_메서드`

    `method_for_inference_heuristics`는 추론 중에 필요할 경우 주어진 메서드의 생성기를 확장합니다.
  * `부모`

    이 객체를 "소유하는" `MethodInstance`(해당되는 경우).
  * `모서리`

    메서드 인스턴스를 무효화해야 하는 포워드 엣지.
  * `min_world`/`max_world`

    이 코드가 추론되었을 당시 유효했던 세계 연령의 범위.

부울 속성:

  * `추론된`

    이것이 타입 추론에 의해 생성되었는지 여부.
  * `인라인 가능`

    이것이 인라인으로 적합해야 하는지 여부.
  * `propagate_inbounds`

    이것이 `@boundscheck` 블록을 생략하기 위한 목적으로 인라인될 때 `@inbounds`를 전파해야 하는지 여부.

`UInt8` 설정:

  * `constprop`

      * 0 = 휴리스틱 사용
      * 1 = 공격적인
      * 2 = 없음
  * `purity` 5 비트 플래그로 구성됨:

      * 0x01 << 0 = 이 방법은 일관되게 반환되거나 종료될 것임을 보장합니다 (`:consistent`)
      * 0x01 << 1 = 이 방법은 외부에서 의미적으로 보이는 부작용이 없습니다 (`:effect_free`)
      * 0x01 << 2 = 이 방법은 예외를 발생시키지 않을 것이 보장됩니다 (`:nothrow`)
      * 0x01 << 3 = 이 방법은 종료될 것이 보장됩니다 (`:terminates_globally`)
      * 0x01 << 4 = 이 메서드 내의 구문적 제어 흐름은 종료될 것임이 보장됩니다 (`:terminates_locally`)

    `Base.@assume_effects`에 대한 자세한 내용은 문서를 참조하세요.
