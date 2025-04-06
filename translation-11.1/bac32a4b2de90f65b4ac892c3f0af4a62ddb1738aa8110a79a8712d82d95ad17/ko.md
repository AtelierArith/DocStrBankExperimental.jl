# Frequently Asked Questions

## General

### Is Julia named after someone or something?

아니요.

### Why don't you compile Matlab/Python/R/… code to Julia?

많은 사람들이 다른 동적 언어의 구문에 익숙하고, 그 언어로 이미 많은 코드가 작성되었기 때문에, 프로그래머가 새로운 언어를 배울 필요 없이 Julia의 모든 성능 이점을 얻기 위해 Matlab 또는 Python 프론트엔드를 Julia 백엔드에 연결하거나 코드를 Julia로 "변환"하지 않은 이유에 대해 궁금해하는 것은 자연스러운 일입니다. 간단하죠?

기본적인 문제는 *줄리아의 컴파일러에 특별한 것이 없다*는 것이다: 우리는 다른 언어 개발자들이 모르는 “비밀 소스”가 없는 일반적인 컴파일러(LLVM)를 사용한다. 실제로, 줄리아의 컴파일러는 다른 동적 언어(예: PyPy 또는 LuaJIT)의 컴파일러보다 많은 면에서 훨씬 간단하다. 줄리아의 성능 이점은 거의 전적으로 그 전방에서 비롯된다: 그 언어 의미론은 [well-written Julia program](@ref man-performance-tips)가 *컴파일러가 효율적인 코드와 메모리 레이아웃을 생성할 수 있는 더 많은 기회를 제공하도록 허용한다*. 만약 당신이 Matlab 또는 Python 코드를 줄리아로 컴파일하려고 한다면, 우리의 컴파일러는 Matlab 또는 Python의 의미론에 의해 제한되어 그 언어에 대한 기존 컴파일러보다 나은 코드를 생성할 수 없을 것이다(아마도 더 나쁠 것이다). 의미론의 핵심 역할은 또한 여러 기존 Python 컴파일러(예: Numba와 Pythran)가 언어의 작은 부분 집합(예: Numpy 배열 및 스칼라에 대한 연산)만 최적화하려고 시도하는 이유이며, 이 부분 집합에 대해서는 그들이 동일한 의미론에 대해 우리가 할 수 있는 것만큼 잘하고 있다. 그 프로젝트에서 일하는 사람들은 믿을 수 없을 만큼 똑똑하고 놀라운 성과를 이루었지만, 해석되도록 설계된 언어에 컴파일러를 맞추는 것은 매우 어려운 문제이다.

줄리아의 장점은 좋은 성능이 "내장" 타입과 연산의 작은 하위 집합에 국한되지 않으며, 고수준의 타입 일반 코드가 임의의 사용자 정의 타입에서 작동하면서도 빠르고 메모리 효율성을 유지할 수 있다는 것입니다. 파이썬과 같은 언어의 타입은 유사한 기능을 위해 컴파일러에 충분한 정보를 제공하지 않기 때문에, 이러한 언어를 줄리아의 프론트엔드로 사용하게 되면 곤란해질 것입니다.

유사한 이유로, 자동 번역을 통해 생성된 줄리아 코드는 일반적으로 읽기 어렵고, 느리며, 비관습적인 코드가 되어 다른 언어에서 줄리아로의 네이티브 포트를 위한 좋은 출발점이 되지 않을 것입니다.

반면에, 언어 *상호 운용성*은 매우 유용합니다: 우리는 Julia에서 다른 언어의 기존 고품질 코드를 활용하고 싶습니다(그리고 그 반대도 마찬가지입니다)! 이를 가능하게 하는 가장 좋은 방법은 트랜스파일러가 아니라 언어 간 호출 기능을 쉽게 하는 것입니다. 우리는 C 및 Fortran 라이브러리를 호출하기 위한 내장 `ccall` 내재 함수부터 Julia를 Python, Matlab, C++ 등과 연결하는 [JuliaInterop](https://github.com/JuliaInterop) 패키지에 이르기까지 이 작업을 위해 열심히 노력해왔습니다.

## [Public API](@id man-api)

### How does Julia define its public API?

줄리아의 공개 [API](https://en.wikipedia.org/wiki/API)는 `Base` 및 표준 라이브러리의 공개 기호에 대한 문서에 설명된 동작입니다. 함수, 타입 및 상수는 공개가 아닌 경우 공개 API의 일부가 아니며, 문서 문자열이 있거나 문서에 설명되어 있더라도 마찬가지입니다. 또한, 공개 기호의 문서화된 동작만이 공개 API의 일부입니다. 공개 기호의 문서화되지 않은 동작은 내부적입니다.

공개 기호는 `public foo` 또는 `export foo`로 표시된 기호입니다.

다른 말로 하면:

  * 문서화된 공용 기호의 동작은 공용 API의 일부입니다.
  * 문서화되지 않은 공용 기호의 동작은 공용 API의 일부가 아닙니다.
  * 문서화된 개인 기호의 동작은 공개 API의 일부가 아닙니다.
  * 비공식 기호의 문서화되지 않은 동작은 공개 API의 일부가 아닙니다.

`names(MyModule)`를 사용하여 모듈의 공개 기호 목록을 완전하게 얻을 수 있습니다.

패키지 저자는 자신의 공개 API를 유사하게 정의하는 것이 권장됩니다.

줄리아의 공개 API에 있는 모든 것은 [SemVer](https://semver.org/)에 의해 보호되며, 따라서 줄리아 2.0 이전에는 제거되거나 의미 있는 파괴적 변경을 받지 않을 것입니다.

### There is a useful undocumented function/type/constant. Can I use it?

Julia를 업데이트하면 비공식 API를 사용하는 경우 코드가 깨질 수 있습니다. 코드가 독립적이라면 프로젝트에 복사하는 것이 좋습니다. 특히 안정적인 패키지에서 복잡한 비공식 API에 의존하고자 한다면, 이를 공개 API로 전환하기 위한 논의를 시작하기 위해 [issue](https://github.com/JuliaLang/julia/issues) 또는 [pull request](https://github.com/JuliaLang/julia/pulls)를 여는 것이 좋습니다. 그러나 Julia의 비공식 구현 세부 사항에 의존하면서 안정적인 공개 인터페이스를 노출하는 패키지를 만드는 시도를 단념하지는 않습니다.

### The documentation is not accurate enough. Can I rely on the existing behavior?

[issue](https://github.com/JuliaLang/julia/issues) 또는 [pull request](https://github.com/JuliaLang/julia/pulls)를 열어 기존 동작을 공개 API로 전환하는 논의를 시작해 주세요.

## Sessions and the REPL

### How do I delete an object in memory?

줄리아에는 MATLAB의 `clear` 함수와 유사한 기능이 없습니다. 한 번 이름이 줄리아 세션(기술적으로는 모듈 `Main`에서)에서 정의되면, 항상 존재합니다.

메모리 사용이 걱정된다면, 항상 더 적은 메모리를 사용하는 객체로 교체할 수 있습니다. 예를 들어, `A`가 더 이상 필요하지 않은 기가바이트 크기의 배열이라면, `A = nothing`을 사용하여 메모리를 해제할 수 있습니다. 메모리는 가비지 컬렉터가 다음에 실행될 때 해제됩니다. 이를 강제로 실행하려면 [`GC.gc()`](@ref Base.GC.gc)를 사용할 수 있습니다. 또한, `A`를 사용하려고 하면 오류가 발생할 가능성이 높습니다. 왜냐하면 대부분의 메서드는 `Nothing` 타입에 대해 정의되어 있지 않기 때문입니다.

### How can I modify the declaration of a type in my session?

아마도 당신은 타입을 정의한 후에 새로운 필드를 추가해야 한다는 것을 깨달았을 것입니다. REPL에서 이를 시도하면 다음과 같은 오류가 발생합니다:

```
ERROR: invalid redefinition of constant MyType
```

모듈 `Main`의 타입은 재정의할 수 없습니다.

새 코드를 개발할 때 불편할 수 있지만, 훌륭한 우회 방법이 있습니다. 모듈은 재정의하여 교체할 수 있으며, 따라서 모든 새 코드를 모듈 안에 감싸면 타입과 상수를 재정의할 수 있습니다. 타입 이름을 `Main`으로 가져온 다음 그곳에서 재정의할 수 있다고 기대할 수는 없지만, 모듈 이름을 사용하여 범위를 해결할 수 있습니다. 다시 말해, 개발 중에는 다음과 같은 워크플로를 사용할 수 있습니다:

```julia
include("mynewcode.jl")              # this defines a module MyModule
obj1 = MyModule.ObjConstructor(a, b)
obj2 = MyModule.somefunction(obj1)
# Got an error. Change something in "mynewcode.jl"
include("mynewcode.jl")              # reload the module
obj1 = MyModule.ObjConstructor(a, b) # old objects are no longer valid, must reconstruct
obj2 = MyModule.somefunction(obj1)   # this time it worked!
obj3 = MyModule.someotherfunction(obj2, c)
...
```

## [Scripting](@id man-scripting)

### How do I check if the current file is being run as the main script?

파일이 `julia file.jl`을 사용하여 메인 스크립트로 실행될 때, 명령줄 인수 처리와 같은 추가 기능을 활성화하고 싶을 수 있습니다. 파일이 이러한 방식으로 실행되고 있는지 확인하는 방법은 `abspath(PROGRAM_FILE) == @__FILE__`가 `true`인지 확인하는 것입니다.

그러나 스크립트와 가져올 수 있는 라이브러리로서 두 가지 역할을 하는 파일을 작성하지 않는 것이 좋습니다. 라이브러리와 스크립트 모두에서 사용할 수 있는 기능이 필요하다면, 라이브러리로 작성한 다음 해당 기능을 별도의 스크립트로 가져오는 것이 더 좋습니다.

### [How do I catch CTRL-C in a script?](@id catch-ctrl-c)

`julia file.jl`를 사용하여 Julia 스크립트를 실행하면 CTRL-C(SIGINT)로 종료하려고 할 때 [`InterruptException`](@ref)가 발생하지 않습니다. Julia 스크립트를 종료하기 전에 특정 코드를 실행하려면, 이는 CTRL-C로 인해 발생할 수도 있고 아닐 수도 있습니다, [`atexit`](@ref)를 사용하세요. 또는 `julia -e 'include(popfirst!(ARGS))' file.jl`를 사용하여 스크립트를 실행하면서 [`try`](@ref) 블록에서 `InterruptException`을 잡을 수 있습니다. 이 전략을 사용하면 [`PROGRAM_FILE`](@ref)가 설정되지 않음을 유의하세요.

### How do I pass options to `julia` using `#!/usr/bin/env`?

`julia`에 옵션을 전달하는 소위 shebang 라인에서, 예를 들어 `#!/usr/bin/env julia --startup-file=no`와 같이, 많은 플랫폼(BSD, macOS, Linux)에서는 커널이 셸과 달리 공백 문자에서 인수를 분할하지 않기 때문에 작동하지 않습니다. 단일 인수 문자열을 공백에서 여러 인수로 분할하는 `env -S` 옵션은 셸과 유사하게 간단한 우회 방법을 제공합니다:

```julia
#!/usr/bin/env -S julia --color=yes --startup-file=no
@show ARGS  # put any Julia code here
```

!!! note
    옵션 `env -S`는 FreeBSD 6.0 (2005), macOS Sierra (2016) 및 GNU/Linux coreutils 8.30 (2018)에서 등장했습니다.


### Why doesn't `run` support `*` or pipes for scripting external programs?

줄리아의 [`run`](@ref) 함수는 외부 프로그램을 *직접* 실행하며, [operating-system shell](https://en.wikipedia.org/wiki/Shell_(computing))를 호출하지 않습니다 (파이썬, R 또는 C와 같은 다른 언어의 `system("...")` 함수와는 다릅니다). 이는 `run`이 `*`의 와일드카드 확장을 수행하지 않음을 의미합니다 (["globbing"](https://en.wikipedia.org/wiki/Glob_(programming))), 또한 [shell pipelines](https://en.wikipedia.org/wiki/Pipeline_(Unix))를 `|` 또는 `>`와 같이 해석하지도 않습니다.

여전히 Julia 기능을 사용하여 글로빙과 파이프라인을 수행할 수 있습니다. 예를 들어, 내장된 [`pipeline`](@ref) 함수는 외부 프로그램과 파일을 체인할 수 있게 해주며, 이는 셸 파이프와 유사하고, [Glob.jl package](https://github.com/vtjnash/Glob.jl)는 POSIX 호환 글로빙을 구현합니다.

물론, `run`에 셸과 명령 문자열을 명시적으로 전달하여 셸을 통해 프로그램을 실행할 수 있습니다. 예를 들어, ```run(`sh -c "ls > files.txt"`)```를 사용하여 Unix [Bourne shell](https://en.wikipedia.org/wiki/Bourne_shell)를 사용할 수 있지만, 일반적으로는 순수 Julia 스크립팅인 ```run(pipeline(`ls`, "files.txt"))```을 선호해야 합니다. 기본적으로 셸을 피하는 이유는 [shelling out sucks](https://julialang.org/blog/2012/03/shelling-out-sucks/): 셸을 통해 프로세스를 시작하는 것은 느리고, 특수 문자 인용에 취약하며, 오류 처리도 좋지 않고, 이식성에 문제가 있기 때문입니다. (Python 개발자들은 [similar conclusion](https://www.python.org/dev/peps/pep-0324/#motivation)에 도달했습니다.)

## Variables and Assignments

### Why am I getting `UndefVarError` from a simple loop?

당신은 다음과 같은 것이 있을 수 있습니다:

```
x = 0
while x < 10
    x += 1
end
```

그리고 대화형 환경(예: Julia REPL)에서는 잘 작동하지만, 스크립트나 다른 파일에서 실행하려고 하면 ```UndefVarError: `x` not defined``` 오류가 발생하는 것을 주목하세요. 발생하는 이유는 Julia가 일반적으로 **로컬 범위에서 전역 변수에 할당할 때 명시적이어야 한다**는 것입니다.

여기서 `x`는 전역 변수이고, `while`은 [local scope](@ref scope-of-variables)를 정의하며, `x += 1`은 해당 지역 범위에서 전역 변수에 대한 할당입니다.

위에서 언급한 바와 같이, Julia(버전 1.5 이상)는 REPL(및 많은 다른 대화형 환경)에서 코드에 대해 `global` 키워드를 생략할 수 있도록 하여 탐색을 간소화합니다(예: 함수를 복사하여 대화형으로 실행). 그러나 파일 내의 코드로 이동하면 Julia는 전역 변수에 대해 보다 규칙적인 접근 방식을 요구합니다. 최소한 세 가지 옵션이 있습니다:

1. 코드를 함수로 넣으세요 (그래서 `x`는 함수 내에서 *지역* 변수가 됩니다). 일반적으로, 전역 스크립트보다 함수를 사용하는 것이 좋은 소프트웨어 공학입니다 (온라인에서 "전역 변수가 나쁜 이유"를 검색하면 많은 설명을 볼 수 있습니다). 줄리아에서 전역 변수는 또한 [slow](@ref man-performance-tips)입니다.
2. 코드를 [`let`](@ref) 블록으로 감싸십시오. (이렇게 하면 `x`가 `let ... end` 문 내에서 지역 변수가 되어 `global`의 필요성을 다시 없앱니다.)
3. 로컬 범위 내에서 `x`를 `global`로 명시적으로 표시한 후 할당합니다. 예: `global x += 1`이라고 작성합니다.

더 많은 설명은 매뉴얼 섹션 [on soft scope](@ref on-soft-scope)에서 찾을 수 있습니다.

## Functions

### I passed an argument `x` to a function, modified it inside that function, but on the outside, the variable `x` is still unchanged. Why?

함수를 다음과 같이 호출한다고 가정해 보겠습니다:

```jldoctest
julia> x = 10
10

julia> function change_value!(y)
           y = 17
       end
change_value! (generic function with 1 method)

julia> change_value!(x)
17

julia> x # x is unchanged!
10
```

줄리아에서 변수 `x`의 바인딩은 `x`를 함수의 인수로 전달함으로써 변경될 수 없습니다. 위의 예제에서 `change_value!(x)`를 호출할 때, `y`는 처음에 `x`의 값인 `10`에 바인딩된 새로 생성된 변수입니다. 그 후 `y`는 상수 `17`에 다시 바인딩되지만, 외부 범위의 변수 `x`는 변경되지 않습니다.

그러나 `x`가 `Array`(또는 다른 *변경 가능한* 유형)의 객체에 바인딩되어 있는 경우, 함수 내에서 `x`를 이 Array에서 "바인딩 해제"할 수는 없지만, 그 내용을 *변경*할 수는 있습니다. 예를 들어:

```jldoctest
julia> x = [1,2,3]
3-element Vector{Int64}:
 1
 2
 3

julia> function change_array!(A)
           A[1] = 5
       end
change_array! (generic function with 1 method)

julia> change_array!(x)
5

julia> x
3-element Vector{Int64}:
 5
 2
 3
```

여기에서 우리는 `change_array!`라는 함수를 만들었습니다. 이 함수는 전달된 배열의 첫 번째 요소에 `5`를 할당합니다(호출 지점에서 `x`에 바인딩되고 함수 내에서는 `A`에 바인딩됨). 함수 호출 후에도 `x`는 여전히 같은 배열에 바인딩되어 있지만, 그 배열의 내용은 변경되었습니다: 변수 `A`와 `x`는 동일한 가변 `Array` 객체를 참조하는 별개의 바인딩이었습니다.

### Can I use `using` or `import` inside a function?

아니요, 함수 내부에 `using` 또는 `import` 문을 사용할 수 없습니다. 모듈을 가져오고 싶지만 특정 함수 또는 함수 집합 내에서만 그 기호를 사용하고 싶다면 두 가지 옵션이 있습니다:

1. `import` 사용:

    ```julia
    import Foo
    function bar(...)
        # ... refer to Foo symbols via Foo.baz ...
    end
    ```

    이것은 모듈 `Foo`를 로드하고 모듈을 참조하는 변수 `Foo`를 정의하지만 현재 네임스페이스로 모듈의 다른 기호를 가져오지 않습니다. `Foo` 기호는 자격이 있는 이름 `Foo.bar` 등으로 참조합니다.
2. 함수를 모듈로 감싸세요:

    ```julia
    module Bar
    export bar
    using Foo
    function bar(...)
        # ... refer to Foo.baz as simply baz ....
    end
    end
    using Bar
    ```

    이것은 `Foo`의 모든 기호를 가져오지만, 오직 모듈 `Bar` 내에서만 그렇습니다.

### What does the `...` operator do?

#### The two uses of the `...` operator: slurping and splatting

많은 줄리아 초보자들은 `...` 연산자의 사용이 혼란스럽다고 느낍니다. `...` 연산자가 혼란스러운 이유 중 하나는 문맥에 따라 두 가지 다른 의미를 갖기 때문입니다.

#### `...` combines many arguments into one argument in function definitions

함수 정의의 맥락에서 `...` 연산자는 여러 가지 다른 인수를 하나의 인수로 결합하는 데 사용됩니다. 여러 가지 다른 인수를 하나의 인수로 결합하기 위한 `...`의 이러한 사용을 슬러핑이라고 합니다:

```jldoctest
julia> function printargs(args...)
           println(typeof(args))
           for (i, arg) in enumerate(args)
               println("Arg #$i = $arg")
           end
       end
printargs (generic function with 1 method)

julia> printargs(1, 2, 3)
Tuple{Int64, Int64, Int64}
Arg #1 = 1
Arg #2 = 2
Arg #3 = 3
```

만약 줄리아가 ASCII 문자를 더 자유롭게 사용했다면, 슬러핑 연산자는 `...` 대신 `<-...`로 작성되었을 것입니다.

#### `...` splits one argument into many different arguments in function calls

함수를 정의할 때 여러 다른 인수를 하나의 인수로 모으기 위해 `...` 연산자를 사용하는 것과 대조적으로, `...` 연산자는 함수 호출의 맥락에서 단일 함수 인수를 여러 다른 인수로 분리하는 데에도 사용됩니다. `...`의 이러한 사용을 스플래팅(splatting)이라고 합니다:

```jldoctest
julia> function threeargs(a, b, c)
           println("a = $a::$(typeof(a))")
           println("b = $b::$(typeof(b))")
           println("c = $c::$(typeof(c))")
       end
threeargs (generic function with 1 method)

julia> x = [1, 2, 3]
3-element Vector{Int64}:
 1
 2
 3

julia> threeargs(x...)
a = 1::Int64
b = 2::Int64
c = 3::Int64
```

만약 줄리아가 ASCII 문자를 더 자유롭게 사용한 언어였다면, 스플래팅 연산자는 `...->`로 작성되었을지도 모른다.

### What is the return value of an assignment?

연산자 `=`는 항상 오른쪽 값을 반환하므로:

```jldoctest
julia> function threeint()
           x::Int = 3.0
           x # returns variable x
       end
threeint (generic function with 1 method)

julia> function threefloat()
           x::Int = 3.0 # returns 3.0
       end
threefloat (generic function with 1 method)

julia> threeint()
3

julia> threefloat()
3.0
```

그리고 유사하게:

```jldoctest
julia> function twothreetup()
           x, y = [2, 3] # assigns 2 to x and 3 to y
           x, y # returns a tuple
       end
twothreetup (generic function with 1 method)

julia> function twothreearr()
           x, y = [2, 3] # returns an array
       end
twothreearr (generic function with 1 method)

julia> twothreetup()
(2, 3)

julia> twothreearr()
2-element Vector{Int64}:
 2
 3
```

## Types, type declarations, and constructors

### [What does "type-stable" mean?](@id man-type-stability)

출력의 유형이 입력의 유형으로부터 예측 가능하다는 것을 의미합니다. 특히, 출력의 유형은 입력의 *값*에 따라 달라질 수 없음을 의미합니다. 다음 코드는 *유형 안정적*이지 않습니다:

```jldoctest
julia> function unstable(flag::Bool)
           if flag
               return 1
           else
               return 1.0
           end
       end
unstable (generic function with 1 method)
```

그것은 인수의 값에 따라 `Int` 또는 [`Float64`](@ref) 중 하나를 반환합니다. 줄리아는 컴파일 타임에 이 함수의 반환 유형을 예측할 수 없기 때문에, 이를 사용하는 모든 계산은 두 가지 유형의 값을 처리할 수 있어야 하며, 이는 빠른 기계 코드를 생성하는 것을 어렵게 만듭니다.

### [Why does Julia give a `DomainError` for certain seemingly-sensible operations?](@id faq-domain-errors)

특정 연산은 수학적으로 의미가 있지만 오류를 발생시킵니다:

```jldoctest
julia> sqrt(-2.0)
ERROR: DomainError with -2.0:
sqrt was called with a negative real argument but will only return a complex result if called with a complex argument. Try sqrt(Complex(x)).
Stacktrace:
[...]
```

이 행동은 타입 안정성 요구 사항의 불편한 결과입니다. [`sqrt`](@ref)의 경우, 대부분의 사용자는 `sqrt(2.0)`이 실수를 반환하기를 원하며, 복소수 `1.4142135623730951 + 0.0im`을 반환하면 불만을 가질 것입니다. `4d61726b646f776e2e436f64652822222c2022737172742229_40726566` 함수를 음수를 전달할 때만 복소수 출력을 전환하도록 작성할 수 있지만(이는 다른 언어에서 `4d61726b646f776e2e436f64652822222c2022737172742229_40726566`가 하는 방식입니다), 그러면 결과는 [type-stable](@ref man-type-stability)가 되지 않으며 `4d61726b646f776e2e436f64652822222c2022737172742229_40726566` 함수의 성능이 저하될 것입니다.

이러한 경우와 다른 경우에, 결과를 표현할 수 있는 *출력 유형*을 수용하겠다는 의사를 전달하는 *입력 유형*을 선택함으로써 원하는 결과를 얻을 수 있습니다:

```jldoctest
julia> sqrt(-2.0+0im)
0.0 + 1.4142135623730951im
```

### How can I constrain or compute type parameters?

The parameters of a [parametric type](@ref Parametric-Types) can hold either types or bits values, and the type itself chooses how it makes use of these parameters. For example, `Array{Float64, 2}` is parameterized by the type `Float64` to express its element type and the integer value `2` to express its number of dimensions.  When defining your own parametric type, you can use subtype constraints to declare that a certain parameter must be a subtype ([`<:`](@ref)) of some abstract type or a previous type parameter.  There is not, however, a dedicated syntax to declare that a parameter must be a *value* of a given type — that is, you cannot directly declare that a dimensionality-like parameter [`isa`](@ref) `Int` within the `struct` definition, for example.  Similarly, you cannot do computations (including simple things like addition or subtraction) on type parameters.  Instead, these sorts of constraints and relationships may be expressed through additional type parameters that are computed and enforced within the type's [constructors](@ref man-constructors).

예를 들어, 다음을 고려하십시오.

```julia
struct ConstrainedType{T,N,N+1} # NOTE: INVALID SYNTAX
    A::Array{T,N}
    B::Array{T,N+1}
end
```

사용자가 세 번째 유형 매개변수가 항상 두 번째 매개변수에 1을 더한 값이 되도록 강제하고 싶어하는 경우, 이는 [inner constructor method](@ref man-inner-constructor-methods)에 의해 확인되는 명시적 유형 매개변수를 사용하여 구현할 수 있습니다(여기서 다른 검사와 결합할 수 있습니다):

```julia
struct ConstrainedType{T,N,M}
    A::Array{T,N}
    B::Array{T,M}
    function ConstrainedType(A::Array{T,N}, B::Array{T,M}) where {T,N,M}
        N + 1 == M || throw(ArgumentError("second argument should have one more axis" ))
        new{T,N,M}(A, B)
    end
end
```

이 검사는 일반적으로 *비용이 들지* 않으며, 컴파일러가 유효한 구체적 유형에 대한 검사를 생략할 수 있습니다. 두 번째 인수도 계산되는 경우, 이 계산을 수행하는 [outer constructor method](@ref man-outer-constructor-methods)를 제공하는 것이 유리할 수 있습니다:

```julia
ConstrainedType(A) = ConstrainedType(A, compute_B(A))
```

### [Why does Julia use native machine integer arithmetic?](@id faq-integer-arithmetic)

줄리아는 정수 계산을 위해 기계 산술을 사용합니다. 이는 `Int` 값의 범위가 제한되어 있으며, 양쪽 끝에서 감싸지므로 정수를 더하거나 빼거나 곱할 때 오버플로우 또는 언더플로우가 발생할 수 있으며, 이로 인해 처음에는 불안할 수 있는 결과가 나올 수 있습니다:

```jldoctest
julia> x = typemax(Int)
9223372036854775807

julia> y = x+1
-9223372036854775808

julia> z = -y
-9223372036854775808

julia> 2*z
0
```

분명히, 이것은 수학적 정수의 동작 방식과는 거리가 멀며, 고급 프로그래밍 언어가 이를 사용자에게 노출하는 것은 이상적이지 않다고 생각할 수 있습니다. 그러나 효율성과 투명성이 중요한 수치 작업에서는 대안이 더 나쁩니다.

하나의 대안으로 고려할 수 있는 것은 각 정수 연산에 대해 오버플로우를 확인하고 결과를 [`Int128`](@ref) 또는 [`BigInt`](@ref)와 같은 더 큰 정수 타입으로 승격하는 것입니다. 불행히도, 이는 모든 정수 연산에 대해 주요 오버헤드를 도입합니다(루프 카운터를 증가시키는 것을 생각해 보세요) – 이는 산술 명령어 후에 런타임 오버플로우 검사를 수행하고 잠재적인 오버플로우를 처리하기 위한 분기로 코드를 생성해야 합니다. 더욱이, 이는 모든 정수 관련 계산이 타입 불안정하게 만들 것입니다. 위에서 언급한 바와 같이, [type-stability is crucial](@ref man-type-stability)는 효율적인 코드 생성을 위한 효과적인 방법입니다. 정수 연산의 결과가 정수일 것이라고 믿을 수 없다면, C와 Fortran 컴파일러가 하는 것처럼 빠르고 간단한 코드를 생성하는 것은 불가능합니다.

이 접근 방식의 변형은 타입 불안정성의 외관을 피하기 위해 `Int`와 [`BigInt`](@ref) 타입을 단일 하이브리드 정수 타입으로 병합하는 것입니다. 이 타입은 결과가 더 이상 머신 정수의 크기에 맞지 않을 때 내부적으로 표현을 변경합니다. 표면적으로는 Julia 코드 수준에서 타입 불안정성을 피하지만, 이 하이브리드 정수 타입을 구현하는 C 코드에 모든 동일한 어려움을 떠넘김으로써 문제를 덮어버리는 것입니다. 이 접근 방식은 *작동할 수* 있으며 많은 경우 꽤 빠르게 만들 수 있지만 몇 가지 단점이 있습니다. 한 가지 문제는 정수와 정수 배열의 메모리 내 표현이 C, Fortran 및 기타 네이티브 머신 정수를 사용하는 언어에서 사용되는 자연 표현과 더 이상 일치하지 않는다는 것입니다. 따라서 이러한 언어와 상호 운용하기 위해서는 결국 네이티브 정수 타입을 도입해야 합니다. 무한한 정수 표현은 고정된 비트 수를 가질 수 없으며, 따라서 고정 크기 슬롯이 있는 배열에 인라인으로 저장될 수 없습니다. 큰 정수 값은 항상 별도의 힙 할당 저장소를 필요로 합니다. 그리고 물론, 어떤 하이브리드 정수 구현을 사용하더라도 항상 성능 함정이 존재합니다. 성능이 예기치 않게 저하되는 상황입니다. 복잡한 표현, C 및 Fortran과의 상호 운용성 부족, 추가 힙 저장소 없이 정수 배열을 표현할 수 없는 점, 예측할 수 없는 성능 특성은 가장 영리한 하이브리드 정수 구현조차도 고성능 수치 작업에 적합하지 않은 선택으로 만듭니다.

하이브리드 정수를 사용하거나 BigInt로 승격하는 대신, 포화 정수 산술을 사용하는 것이 대안이 될 수 있습니다. 여기서 가장 큰 정수 값에 더할 때 값이 변경되지 않고, 가장 작은 정수 값에서 빼면 마찬가지로 값이 변경되지 않습니다. 이것이 바로 Matlab™에서 수행하는 방식입니다:

```
>> int64(9223372036854775807)

ans =

  9223372036854775807

>> int64(9223372036854775807) + 1

ans =

  9223372036854775807

>> int64(-9223372036854775808)

ans =

 -9223372036854775808

>> int64(-9223372036854775808) - 1

ans =

 -9223372036854775808
```

처음에는 9223372036854775807이 -9223372036854775808보다 9223372036854775808에 훨씬 더 가깝기 때문에 합리적으로 보입니다. 정수는 여전히 C와 Fortran과 호환되는 자연스러운 방식으로 고정 크기로 표현됩니다. 그러나 포화 정수 산술은 심각한 문제를 안고 있습니다. 첫 번째이자 가장 명백한 문제는 이것이 기계 정수 산술이 작동하는 방식이 아니기 때문에 포화 연산을 구현하려면 각 기계 정수 연산 후에 언더플로우 또는 오버플로우를 확인하고 결과를 적절하게 [`typemin(Int)`](@ref) 또는 [`typemax(Int)`](@ref)로 교체하는 명령어를 방출해야 합니다. 이것만으로도 각 정수 연산이 단일의 빠른 명령어에서 반 다스틴 명령어로 확장되며, 아마도 분기를 포함할 것입니다. 아프네요. 하지만 더 나빠집니다 – 포화 정수 산술은 결합 법칙을 따르지 않습니다. 이 Matlab 계산을 고려해 보세요:

```
>> n = int64(2)^62
4611686018427387904

>> n + (n - 1)
9223372036854775807

>> (n + n) - 1
9223372036854775806
```

이로 인해 많은 기본 정수 알고리즘을 작성하기가 어려워지는데, 이는 많은 일반적인 기법들이 오버플로우가 있는 기계 덧셈이 *결합법칙*이라는 사실에 의존하기 때문입니다. Julia에서 정수 값 `lo`와 `hi` 사이의 중간값을 찾는 표현식 `(lo + hi) >>> 1`을 고려해 보십시오:

```jldoctest
julia> n = 2^62
4611686018427387904

julia> (n + 2n) >>> 1
6917529027641081856
```

보세요? 문제 없습니다. `2^62`와 `2^63` 사이의 올바른 중간값입니다. `n + 2n`이 -4611686018427387904임에도 불구하고요. 이제 Matlab에서 시도해 보세요:

```
>> (n + 2*n)/2

ans =

  4611686018427387904
```

오류입니다. Matlab에 `>>>` 연산자를 추가하는 것은 도움이 되지 않습니다. 왜냐하면 `n`과 `2n`을 더할 때 발생하는 포화가 올바른 중간값을 계산하는 데 필요한 정보를 이미 파괴했기 때문입니다.

비연관성이 프로그래머에게 불행한 것일 뿐만 아니라, 이러한 기술을 위해 그것에 의존할 수 없는 프로그래머에게도 불행한 일입니다. 또한, 이는 컴파일러가 정수 산술을 최적화하기 위해 하고자 하는 거의 모든 것을 무력화합니다. 예를 들어, 줄리아의 정수는 일반적인 기계 정수 산술을 사용하므로, LLVM은 `f(k) = 5k-1`과 같은 간단한 작은 함수들을 공격적으로 최적화할 수 있습니다. 이 함수의 기계 코드는 다음과 같습니다:

```julia-repl
julia> code_native(f, Tuple{Int})
  .text
Filename: none
  pushq %rbp
  movq  %rsp, %rbp
Source line: 1
  leaq  -1(%rdi,%rdi,4), %rax
  popq  %rbp
  retq
  nopl  (%rax,%rax)
```

함수의 실제 본체는 단일 `leaq` 명령어로, 정수 곱셈과 덧셈을 한 번에 계산합니다. `f`가 다른 함수에 인라인될 때 이는 더욱 유리합니다:

```julia-repl
julia> function g(k, n)
           for i = 1:n
               k = f(k)
           end
           return k
       end
g (generic function with 1 methods)

julia> code_native(g, Tuple{Int,Int})
  .text
Filename: none
  pushq %rbp
  movq  %rsp, %rbp
Source line: 2
  testq %rsi, %rsi
  jle L26
  nopl  (%rax)
Source line: 3
L16:
  leaq  -1(%rdi,%rdi,4), %rdi
Source line: 2
  decq  %rsi
  jne L16
Source line: 5
L26:
  movq  %rdi, %rax
  popq  %rbp
  retq
  nop
```

`f`가 인라인으로 처리되기 때문에 루프 본문은 단일 `leaq` 명령어로 끝납니다. 다음으로, 루프 반복 횟수를 고정하면 어떤 일이 발생하는지 살펴보겠습니다:

```julia-repl
julia> function g(k)
           for i = 1:10
               k = f(k)
           end
           return k
       end
g (generic function with 2 methods)

julia> code_native(g,(Int,))
  .text
Filename: none
  pushq %rbp
  movq  %rsp, %rbp
Source line: 3
  imulq $9765625, %rdi, %rax    # imm = 0x9502F9
  addq  $-2441406, %rax         # imm = 0xFFDABF42
Source line: 5
  popq  %rbp
  retq
  nopw  %cs:(%rax,%rax)
```

컴파일러는 정수 덧셈과 곱셈이 결합법칙을 따르고 곱셈이 덧셈에 대해 분배법칙을 따른다는 것을 알고 있기 때문에 – 이는 포화 산술에서는 사실이 아닙니다 – 전체 루프를 단지 곱셈과 덧셈으로 최적화할 수 있습니다. 포화 산술은 이러한 종류의 최적화를 완전히 무력화합니다. 왜냐하면 각 루프 반복에서 결합법칙과 분배법칙이 실패할 수 있어 실패가 발생하는 반복에 따라 다른 결과를 초래할 수 있기 때문입니다. 컴파일러는 루프를 펼칠 수 있지만, 여러 연산을 더 적은 동등한 연산으로 대수적으로 축소할 수는 없습니다.

정수 산술이 조용히 오버플로우되는 것에 대한 가장 합리적인 대안은 모든 곳에서 체크된 산술을 수행하여 더하기, 빼기 및 곱하기가 오버플로우될 때 오류를 발생시키고, 값이 올바르지 않은 값을 생성하는 것입니다. 이 [blog post](https://danluu.com/integer-overflow/)에서 Dan Luu는 이를 분석하고 이 접근 방식이 이론적으로는 사소한 비용을 가져야 하지만, 실제로는 추가된 오버플로우 체크를 최적화하지 않는 컴파일러(LLVM 및 GCC)로 인해 상당한 비용이 발생한다고 발견했습니다. 만약 이것이 미래에 개선된다면, 우리는 Julia에서 체크된 정수 산술을 기본값으로 설정하는 것을 고려할 수 있지만, 현재로서는 오버플로우의 가능성과 함께 살아가야 합니다.

그동안 오버플로우 안전한 정수 연산은 [SaferIntegers.jl](https://github.com/JeffreySarnoff/SaferIntegers.jl)와 같은 외부 라이브러리를 사용하여 달성할 수 있습니다. 앞서 언급했듯이, 이러한 라이브러리를 사용하면 체크된 정수 타입을 사용하는 코드의 실행 시간이 크게 증가합니다. 그러나 제한된 사용의 경우, 모든 정수 연산에 사용되는 것보다 훨씬 덜 문제가 됩니다. 논의의 진행 상황은 [here](https://github.com/JuliaLang/julia/issues/855)를 통해 확인할 수 있습니다.

### What are the possible causes of an `UndefVarError` during remote execution?

오류가 나타내는 바와 같이, 원격 노드에서 `UndefVarError`의 즉각적인 원인은 해당 이름으로 바인딩이 존재하지 않기 때문입니다. 가능한 원인 몇 가지를 살펴보겠습니다.

```julia-repl
julia> module Foo
           foo() = remotecall_fetch(x->x, 2, "Hello")
       end

julia> Foo.foo()
ERROR: On worker 2:
UndefVarError: `Foo` not defined in `Main`
Stacktrace:
[...]
```

클로저 `x->x`는 `Foo`에 대한 참조를 가지고 있으며, `Foo`가 노드 2에서 사용할 수 없기 때문에 `UndefVarError`가 발생합니다.

`Main` 이외의 모듈에서의 전역 변수는 원격 노드에 값으로 직렬화되지 않습니다. 오직 참조만 전송됩니다. 전역 바인딩을 생성하는 함수( `Main` 이외의 경우)는 나중에 `UndefVarError`가 발생할 수 있습니다.

```julia-repl
julia> @everywhere module Foo
           function foo()
               global gvar = "Hello"
               remotecall_fetch(()->gvar, 2)
           end
       end

julia> Foo.foo()
ERROR: On worker 2:
UndefVarError: `gvar` not defined in `Main.Foo`
Stacktrace:
[...]
```

위의 예에서 `@everywhere module Foo`는 모든 노드에서 `Foo`를 정의했습니다. 그러나 `Foo.foo()` 호출은 로컬 노드에서 새로운 전역 바인딩 `gvar`를 생성했지만, 이는 노드 2에서 발견되지 않아 `UndefVarError` 오류가 발생했습니다.

모듈 `Main` 아래에서 생성된 전역 변수에는 적용되지 않음을 유의하십시오. 모듈 `Main` 아래의 전역 변수는 직렬화되며 원격 노드에서 `Main` 아래에 새로운 바인딩이 생성됩니다.

```julia-repl
julia> gvar_self = "Node1"
"Node1"

julia> remotecall_fetch(()->gvar_self, 2)
"Node1"

julia> remotecall_fetch(varinfo, 2)
name          size summary
––––––––– –––––––– –––––––
Base               Module
Core               Module
Main               Module
gvar_self 13 bytes String
```

이것은 `function` 또는 `struct` 선언에는 적용되지 않습니다. 그러나 전역 변수에 바인딩된 익명 함수는 아래에서 볼 수 있듯이 직렬화됩니다.

```julia-repl
julia> bar() = 1
bar (generic function with 1 method)

julia> remotecall_fetch(bar, 2)
ERROR: On worker 2:
UndefVarError: `#bar` not defined in `Main`
[...]

julia> anon_bar  = ()->1
(::#21) (generic function with 1 method)

julia> remotecall_fetch(anon_bar, 2)
1
```

## Troubleshooting "method not matched": parametric type invariance and `MethodError`s

### Why doesn't it work to declare `foo(bar::Vector{Real}) = 42` and then call `foo([1])`?

시도해보면 알 수 있듯이, 결과는 `MethodError`입니다:

```jldoctest
julia> foo(x::Vector{Real}) = 42
foo (generic function with 1 method)

julia> foo([1])
ERROR: MethodError: no method matching foo(::Vector{Int64})
The function `foo` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  foo(!Matched::Vector{Real})
   @ Main none:1

Stacktrace:
[...]
```

이것은 `Vector{Real}`이 `Vector{Int}`의 슈퍼타입이 아니기 때문입니다! 이 문제는 `foo(bar::Vector{T}) where {T<:Real}`와 같은 방법으로 해결할 수 있습니다 (정적 매개변수 `T`가 함수 본문에서 필요하지 않은 경우 짧은 형식 `foo(bar::Vector{<:Real})`를 사용할 수 있습니다). `T`는 와일드 카드입니다: 먼저 그것이 Real의 서브타입이어야 한다고 지정한 다음, 해당 유형의 요소를 가진 Vector를 함수가 받는다고 지정합니다.

이 동일한 문제는 `Vector`뿐만 아니라 모든 복합 유형 `Comp`에 해당합니다. 만약 `Comp`가 유형 `Y`의 매개변수를 선언하고 있다면, 매개변수가 유형 `X<:Y`인 다른 유형 `Comp2`는 `Comp`의 하위 유형이 아닙니다. 이것은 유형 불변성(type-invariance)입니다(대조적으로, Tuple은 그 매개변수에서 유형 공변성(type-covariance)을 가집니다). 이러한 내용에 대한 더 많은 설명은 [Parametric Composite Types](@ref man-parametric-composite-types)를 참조하세요.

### Why does Julia use `*` for string concatenation? Why not `+` or something else?

[main argument](@ref man-concatenation)에 대한 `+`의 단점은 문자열 연결이 교환법칙이 성립하지 않는다는 점입니다. 반면 `+`는 일반적으로 교환법칙이 성립하는 연산자로 사용됩니다. Julia 커뮤니티는 다른 언어들이 다른 연산자를 사용한다는 점을 인식하고 있으며, `*`가 일부 사용자에게는 낯설 수 있지만, 특정 대수적 성질을 전달합니다.

`string(...)`를 사용하여 문자열(및 문자열로 변환된 다른 값)을 연결할 수 있습니다. 마찬가지로, `repeat`는 문자열을 반복하는 데 `^` 대신 사용할 수 있습니다. [interpolation syntax](@ref string-interpolation)는 문자열을 구성하는 데에도 유용합니다.

## Packages and Modules

### What is the difference between "using" and "import"?

`using`과 `import` 사이에는 여러 가지 차이가 있지만(자세한 내용은 [Modules section](https://docs.julialang.org/en/v1/manual/modules/#modules) 참조), 처음에는 직관적이지 않을 수 있는 중요한 차이가 있습니다. 표면적으로(즉, 문법적으로) 매우 사소해 보일 수 있습니다. `using`으로 모듈을 로드할 때는 `function Foo.bar(...`라고 말해야 모듈 `Foo`의 함수 `bar`를 새로운 메서드로 확장할 수 있지만, `import Foo.bar`를 사용할 경우에는 `function bar(...`라고만 말하면 자동으로 모듈 `Foo`의 함수 `bar`가 확장됩니다.

이것이 별도의 구문을 가질 만큼 중요한 이유는, 존재하는지 몰랐던 함수를 우연히 확장하고 싶지 않기 때문입니다. 이는 버그를 쉽게 유발할 수 있습니다. 일반적으로 문자열이나 정수와 같은 공통 유형을 사용하는 메서드에서 가장 많이 발생할 수 있습니다. 왜냐하면 당신과 다른 모듈 모두 그러한 공통 유형을 처리하는 메서드를 정의할 수 있기 때문입니다. `import`를 사용하면, 다른 모듈의 `bar(s::AbstractString)` 구현을 당신의 새로운 구현으로 대체하게 되며, 이는 완전히 다른 작업을 수행할 수 있고, 그로 인해 모듈 Foo의 다른 함수들이 bar를 호출하는 데 의존하는 모든/많은 미래의 사용이 깨질 수 있습니다.

## Nothingness and missing values

### [How does "null", "nothingness" or "missingness" work in Julia?](@id faq-nothing)

많은 언어(예: C와 Java)와 달리, Julia 객체는 기본적으로 "null"이 될 수 없습니다. 참조(변수, 객체 필드 또는 배열 요소)가 초기화되지 않은 경우, 이를 접근하면 즉시 오류가 발생합니다. 이 상황은 [`isdefined`](@ref) 또는 [`isassigned`](@ref Base.isassigned) 함수를 사용하여 감지할 수 있습니다.

일부 함수는 부작용만을 위해 사용되며, 값을 반환할 필요가 없습니다. 이러한 경우 관례적으로 `nothing` 값을 반환하는데, 이는 `Nothing` 타입의 단일 객체입니다. 이는 필드가 없는 일반적인 타입으로, 이 관례와 REPL이 이를 위해 아무것도 출력하지 않는 것 외에는 특별한 점이 없습니다. 그렇지 않으면 값을 가지지 않는 일부 언어 구성 요소도 `nothing`을 생성합니다. 예를 들어 `if false; end`가 있습니다.

값 `x`가 타입 `T`인 경우가 가끔만 존재하는 상황에서는 `Union{T, Nothing}` 타입을 함수 인수, 객체 필드 및 배열 요소 타입에 사용할 수 있습니다. 이는 다른 언어에서 [`Nullable`, `Option` or `Maybe`](https://en.wikipedia.org/wiki/Nullable_type)와 동등합니다. 값 자체가 `nothing`일 수 있는 경우(특히 `T`가 `Any`일 때)에는 `Union{Some{T}, Nothing}` 타입이 더 적합합니다. 이 경우 `x == nothing`은 값의 부재를 나타내고, `x == Some(nothing)`은 `nothing`과 같은 값을 가진 존재를 나타냅니다. [`something`](@ref) 함수는 `Some` 객체를 언래핑하고 `nothing` 인수 대신 기본값을 사용할 수 있게 해줍니다. 컴파일러는 `Union{T, Nothing}` 인수나 필드로 작업할 때 효율적인 코드를 생성할 수 있다는 점에 유의하세요.

통계적 의미에서 결측 데이터를 나타내기 위해(`R`의 `NA` 또는 `SQL`의 `NULL`), [`missing`](@ref) 객체를 사용하세요. 더 자세한 내용은 [`Missing Values`](@ref missing) 섹션을 참조하세요.

일부 언어에서는 빈 튜플(`()`)이 무의 상징적인 형태로 간주됩니다. 그러나 줄리아에서는 이것을 단순히 값이 0인 일반 튜플로 생각하는 것이 가장 좋습니다.

빈(또는 "바닥") 타입은 `Union{}`(빈 유니온 타입)으로 표기되며, 값이 없고 서브타입(자신을 제외하고)이 없는 타입입니다. 일반적으로 이 타입을 사용할 필요는 없습니다.

## Memory

### Why does `x += y` allocate memory when `x` and `y` are arrays?

줄리아에서 `x += y`는 하강 과정에서 `x = x + y`로 대체됩니다. 배열의 경우, 이는 결과를 `x`와 동일한 메모리 위치에 저장하는 대신 결과를 저장하기 위해 새로운 배열을 할당하게 됩니다. `x`를 변형하고 싶다면, 각 요소를 개별적으로 업데이트하기 위해 `x .+= y`를 사용하세요.

이러한 행동이 일부 사람들에게 놀라울 수 있지만, 선택은 의도적입니다. 주요 이유는 줄리아 내에서 불변 객체가 존재하기 때문이며, 이는 생성된 후에는 값을 변경할 수 없습니다. 실제로 숫자는 불변 객체입니다; `x = 5; x += 1`이라는 문장은 `5`의 의미를 수정하지 않고, `x`에 바인딩된 값을 수정합니다. 불변 객체의 경우, 값을 변경하는 유일한 방법은 재할당하는 것입니다.

조금 더 확장하기 위해, 다음 함수를 고려해 보십시오:

```julia
function power_by_squaring(x, n::Int)
    ispow2(n) || error("This implementation only works for powers of 2")
    while n >= 2
        x *= x
        n >>= 1
    end
    x
end
```

`x = 5; y = power_by_squaring(x, 4)`와 같은 호출 후에는 예상 결과인 `x == 5 && y == 625`를 얻을 수 있습니다. 그러나 이제 `*=`가 행렬과 함께 사용될 때 왼쪽 변수를 변형한다고 가정해 보겠습니다. 두 가지 문제가 발생할 것입니다:

  * 일반 정사각형 행렬의 경우, `A = A*B`는 임시 저장소 없이 구현할 수 없습니다: `A[1,1]`는 오른쪽에서 사용하기 전에 왼쪽에 저장되기 위해 계산되고 저장됩니다.
  * 임시 변수를 할당할 의향이 있다고 가정해 보겠습니다(이는 `*=`를 제자리에서 작동하게 만드는 대부분의 목적을 없애게 됩니다). `x`의 가변성을 활용한다면, 이 함수는 가변 입력과 불변 입력에 대해 다르게 동작할 것입니다. 특히, 불변 `x`의 경우, 호출 후에 (일반적으로) `y != x`가 되지만, 가변 `x`의 경우에는 `y == x`가 됩니다.

일반 프로그래밍 지원이 다른 방법(예: 브로드캐스팅 또는 명시적 루프 사용)으로 달성할 수 있는 잠재적인 성능 최적화보다 더 중요하다고 여겨지기 때문에, `+=` 및 `*=`와 같은 연산자는 새로운 값을 재바인딩하여 작동합니다.

## [Asynchronous IO and concurrent synchronous writes](@id faq-async-io)

### Why do concurrent writes to the same stream result in inter-mixed output?

스트리밍 I/O API는 동기식이지만, 기본 구현은 완전히 비동기식입니다.

출력된 내용을 고려하십시오:

```jldoctest
julia> @sync for i in 1:3
           @async write(stdout, string(i), " Foo ", " Bar ")
       end
123 Foo  Foo  Foo  Bar  Bar  Bar
```

이것은 `write` 호출이 동기적이지만, 각 인수의 쓰기가 해당 I/O의 일부가 완료되기를 기다리는 동안 다른 작업에 양보하기 때문에 발생합니다.

`print`와 `println`은 호출 중에 스트림을 "잠급니다". 따라서 위의 예제에서 `write`를 `println`으로 변경하면 다음과 같은 결과가 나타납니다:

```jldoctest
julia> @sync for i in 1:3
           @async println(stdout, string(i), " Foo ", " Bar ")
       end
1 Foo  Bar
2 Foo  Bar
3 Foo  Bar
```

`ReentrantLock`를 사용하여 쓰기를 잠글 수 있습니다:

```jldoctest
julia> l = ReentrantLock();

julia> @sync for i in 1:3
           @async begin
               lock(l)
               try
                   write(stdout, string(i), " Foo ", " Bar ")
               finally
                   unlock(l)
               end
           end
       end
1 Foo  Bar 2 Foo  Bar 3 Foo  Bar
```

## Arrays

### [What are the differences between zero-dimensional arrays and scalars?](@id faq-array-0dim)

제로 차원 배열은 `Array{T,0}` 형태의 배열입니다. 이들은 스칼라와 유사하게 동작하지만 중요한 차이점이 있습니다. 이들은 배열의 일반적인 정의를 고려할 때 논리적으로 의미가 있는 특별한 경우이기 때문에 특별히 언급할 가치가 있습니다. 다음 줄은 제로 차원 배열을 정의합니다:

```
julia> A = zeros()
0-dimensional Array{Float64,0}:
0.0
```

이 예제에서 `A`는 하나의 요소를 포함하는 가변 컨테이너로, `A[] = 1.0`으로 설정할 수 있으며 `A[]`로 검색할 수 있습니다. 모든 0차원 배열은 동일한 크기(`size(A) == ()`)와 길이(`length(A) == 1`)를 가집니다. 특히, 0차원 배열은 비어 있지 않습니다. 이것이 직관적이지 않다고 생각되면, 줄리아의 정의를 이해하는 데 도움이 될 수 있는 몇 가지 아이디어가 있습니다.

  * 제로 차원 배열은 벡터의 "선"과 행렬의 "면"에 해당하는 "점"입니다. 선이 면적이 없지만 여전히 사물의 집합을 나타내는 것처럼, 점은 길이나 어떤 차원도 없지만 여전히 사물을 나타냅니다.
  * 우리는 `prod(())`를 1로 정의하며, 배열의 총 요소 수는 크기의 곱입니다. 0차원 배열의 크기는 `()`이며, 따라서 그 길이는 `1`입니다.
  * 제로 차원 배열은 인덱싱할 수 있는 차원이 없으며, 단순히 `A[]`입니다. 다른 모든 배열 차원과 마찬가지로 "후행 1" 규칙을 적용할 수 있으므로, 실제로 `A[1]`, `A[1,1]` 등으로 인덱싱할 수 있습니다; [Omitted and extra indices](@ref)를 참조하세요.

일반 스칼라와의 차이를 이해하는 것도 중요합니다. 스칼라는 변경할 수 없는 컨테이너입니다(비록 반복 가능하고 `length`, `getindex`와 같은 것들을 정의하지만, 예를 들어 `1[] == 1`입니다). 특히, `x = 0.0`이 스칼라로 정의되면, `x[] = 1.0`을 통해 그 값을 변경하려고 시도하는 것은 오류입니다. 스칼라 `x`는 `fill(x)`를 통해 그것을 포함하는 0차원 배열로 변환될 수 있으며, 반대로 0차원 배열 `a`는 `a[]`를 통해 포함된 스칼라로 변환될 수 있습니다. 또 다른 차이점은 스칼라가 `2 * rand(2,2)`와 같은 선형 대수 연산에 참여할 수 있지만, 0차원 배열 `fill(2) * rand(2,2)`와의 유사한 연산은 오류라는 것입니다.

### Why are my Julia benchmarks for linear algebra operations different from other languages?

간단한 벤치마크를 통해 선형 대수의 기본 요소를 찾을 수 있습니다.

```julia
using BenchmarkTools
A = randn(1000, 1000)
B = randn(1000, 1000)
@btime $A \ $B
@btime $A * $B
```

다른 언어인 Matlab이나 R과 비교할 때 다를 수 있습니다.

이러한 작업이 관련 BLAS 함수에 대한 매우 얇은 래퍼이기 때문에 불일치의 이유는 매우 가능성이 높습니다.

1. 각 언어가 사용하는 BLAS 라이브러리,
2. 동시 스레드 수.

Julia는 OpenBLAS의 자체 복사본을 컴파일하고 사용하며, 현재 스레드는 `8`(또는 코어 수)로 제한되어 있습니다.

Modifying OpenBLAS settings or compiling Julia with a different BLAS library, eg [Intel MKL](https://software.intel.com/en-us/mkl), may provide performance improvements. You can use [MKL.jl](https://github.com/JuliaComputing/MKL.jl), a package that makes Julia's linear algebra use Intel MKL BLAS and LAPACK instead of OpenBLAS, or search the discussion forum for suggestions on how to set this up manually. Note that Intel MKL cannot be bundled with Julia, as it is not open source.

## Computing cluster

### How do I manage precompilation caches in distributed file systems?

고성능 컴퓨팅(HPC) 시설에서 공유 파일 시스템을 사용할 때 Julia를 사용하는 경우, 공유 저장소를 사용하는 것이 권장됩니다(환경 변수 [`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH)를 통해). Julia v1.10부터는 기능적으로 유사한 작업자에서 여러 Julia 프로세스가 동일한 저장소를 사용하여 pidfile 잠금을 통해 조정되어, 다른 프로세스가 대기하는 동안 하나의 프로세스에서만 사전 컴파일 작업을 수행합니다. 사전 컴파일 프로세스는 프로세스가 사전 컴파일 중인지 또는 다른 프로세스를 기다리고 있는지를 나타냅니다. 비대화형인 경우 메시지는 `@debug`를 통해 전달됩니다.

그러나 이진 코드의 캐싱으로 인해 v1.9 이후 캐시 거부가 더 엄격해졌으며, 사용자는 HPC 환경 전반에서 사용할 수 있는 단일 캐시를 얻기 위해 [`JULIA_CPU_TARGET`](@ref JULIA_CPU_TARGET) 환경 변수를 적절하게 설정해야 할 수 있습니다.

## Julia Releases

### Do I want to use the Stable, LTS, or nightly version of Julia?

Julia의 안정 버전은 Julia의 최신 릴리스 버전으로, 대부분의 사람들이 실행하고 싶어하는 버전입니다. 이 버전은 성능 향상을 포함한 최신 기능을 갖추고 있습니다. Julia의 안정 버전은 [SemVer](https://semver.org/)에 따라 v1.x.y로 버전이 매겨집니다. 새로운 안정 버전에 해당하는 Julia의 새로운 마이너 릴리스는 몇 주간의 테스트 후 약 4-5개월마다 이루어집니다. LTS 버전과 달리 안정 버전은 다른 안정 버전의 Julia가 릴리스된 후에는 일반적으로 버그 수정이 이루어지지 않습니다. 그러나 다음 안정 릴리스로의 업그레이드는 항상 가능하며, 각 Julia v1.x 릴리스는 이전 버전용으로 작성된 코드를 계속 실행할 수 있습니다.

LTS(장기 지원) 버전의 Julia는 매우 안정적인 코드 기반을 원하신다면 선호하실 수 있습니다. 현재 LTS 버전의 Julia는 SemVer에 따라 v1.6.x로 버전이 매겨져 있으며, 이 브랜치는 새로운 LTS 브랜치가 선택될 때까지 버그 수정 업데이트를 계속 받을 것입니다. 그 시점 이후로 v1.6.x 시리즈는 더 이상 정기적인 버그 수정을 받지 않으며, 가장 보수적인 사용자를 제외한 모든 사용자에게는 새로운 LTS 버전 시리즈로 업그레이드할 것을 권장합니다. 패키지 개발자로서, LTS 버전을 위해 개발하는 것이 패키지를 사용할 수 있는 사용자 수를 극대화하는 데 유리할 수 있습니다. SemVer에 따라 v1.0을 위해 작성된 코드는 모든 미래의 LTS 및 안정적인 버전에서도 계속 작동합니다. 일반적으로 LTS를 목표로 하더라도, 최신 안정적인 버전에서 코드를 개발하고 실행하여 성능 향상의 이점을 누릴 수 있습니다. 단, 새로운 기능(추가된 라이브러리 함수나 새로운 메서드 등)을 사용하지 않는 한에서 가능합니다.

당신은 최신 언어 업데이트를 활용하고 싶고, 오늘 사용 가능한 버전이 가끔 실제로 작동하지 않는 것에 개의치 않는다면 Julia의 야간 버전을 선호할 수 있습니다. 이름에서 알 수 있듯이, 야간 버전의 릴리스는 대략 매일 밤 이루어집니다(빌드 인프라의 안정성에 따라 다름). 일반적으로 야간 릴리스는 사용하기에 꽤 안전합니다—당신의 코드는 불이 붙지 않을 것입니다. 그러나 가끔 회귀나 문제들이 발생할 수 있으며, 이는 더 철저한 사전 릴리스 테스트가 이루어질 때까지 발견되지 않을 수 있습니다. 당신은 릴리스가 이루어지기 전에 사용 사례에 영향을 미치는 그러한 회귀가 잡히도록 야간 버전에서 테스트해 볼 수 있습니다.

마지막으로, 스스로 소스에서 Julia를 빌드하는 것도 고려할 수 있습니다. 이 옵션은 주로 명령줄에 익숙하거나 배우는 데 관심이 있는 개인을 위한 것입니다. 만약 이 설명이 당신에게 해당된다면, 우리의 [guidelines for contributing](https://github.com/JuliaLang/julia/blob/master/CONTRIBUTING.md)를 읽는 것에도 관심이 있을 수 있습니다.

각 다운로드 유형에 대한 링크는 [https://julialang.org/downloads/](https://julialang.org/downloads/)의 다운로드 페이지에서 찾을 수 있습니다. 모든 버전의 Julia가 모든 플랫폼에서 제공되는 것은 아닙니다.

### How can I transfer the list of installed packages after updating my version of Julia?

각 마이너 버전의 Julia는 고유한 기본 [environment](https://docs.julialang.org/en/v1/manual/code-loading/#Environments-1)을 가지고 있습니다. 따라서 새로운 마이너 버전의 Julia를 설치하면 이전 마이너 버전에서 추가한 패키지는 기본적으로 사용할 수 없습니다. 특정 Julia 버전의 환경은 `.julia/environments/`에서 버전 번호와 일치하는 폴더에 있는 `Project.toml` 및 `Manifest.toml` 파일에 의해 정의됩니다. 예를 들어, `.julia/environments/v1.3`입니다.

새로운 마이너 버전의 Julia, 예를 들어 `1.4`를 설치하고 이전 버전(예: `1.3`)과 동일한 패키지를 기본 환경에서 사용하고 싶다면, `1.3` 폴더의 `Project.toml` 파일 내용을 `1.4`로 복사할 수 있습니다. 그런 다음 새로운 Julia 버전의 세션에서 `]` 키를 눌러 "패키지 관리 모드"로 들어가고, 다음 명령어를 실행합니다: [`instantiate`](https://julialang.github.io/Pkg.jl/v1/api/#Pkg.instantiate).

이 작업은 복사된 파일에서 대상 Julia 버전과 호환되는 일련의 유효한 패키지를 해결하고, 적절한 경우 이를 설치하거나 업데이트합니다. 이전 Julia 버전에서 사용하던 패키지 세트뿐만 아니라 버전도 재현하고 싶다면, Pkg 명령어 `instantiate`를 실행하기 전에 `Manifest.toml` 파일도 복사해야 합니다. 그러나 패키지가 호환성 제약을 정의할 수 있으므로 Julia 버전을 변경하면 `1.3`에서 사용하던 정확한 버전 세트가 `1.4`에서 작동하지 않을 수 있습니다.
