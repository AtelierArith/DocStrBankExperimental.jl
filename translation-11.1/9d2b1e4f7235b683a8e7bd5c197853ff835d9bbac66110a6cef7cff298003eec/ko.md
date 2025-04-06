# [Missing Values](@id missing)

줄리아는 통계적 의미에서 결측값을 표현하는 지원을 제공합니다. 이는 관측치에서 변수에 대한 값이 없지만 이론적으로 유효한 값이 존재하는 상황을 위한 것입니다. 결측값은 [`missing`](@ref) 객체를 통해 표현되며, 이는 [`Missing`](@ref) 유형의 단일 인스턴스입니다. `missing`은 [`NULL` in SQL](https://en.wikipedia.org/wiki/NULL_(SQL)) 및 [`NA` in R](https://cran.r-project.org/doc/manuals/r-release/R-lang.html#NA-handling)와 동등하며 대부분의 상황에서 이들과 유사하게 동작합니다.

## Propagation of Missing Values

`missing` 값은 표준 수학 연산자와 함수에 전달될 때 *자동으로* 전파됩니다. 이러한 함수의 경우, 피연산자 중 하나의 값에 대한 불확실성은 결과에 대한 불확실성을 유발합니다. 실제로, `missing` 값을 포함하는 수학 연산은 일반적으로 `missing`을 반환합니다:

```jldoctest
julia> missing + 1
missing

julia> "a" * missing
missing

julia> abs(missing)
missing
```

`missing`는 일반적인 Julia 객체이므로, 이 전파 규칙은 이 동작을 구현하기로 선택한 함수에만 적용됩니다. 이는 다음과 같이 달성할 수 있습니다:

  * `Missing` 유형의 인수에 대해 정의된 특정 메서드를 추가합니다.
  * 이러한 유형의 인수를 수용하고, 이를 전파하는 함수에 전달하는 것(표준 수학 연산자와 같은).

패키지는 새로운 함수를 정의할 때 누락된 값을 전파하는 것이 의미가 있는지 고려해야 하며, 이 경우 적절하게 메서드를 정의해야 합니다. `Missing` 유형의 인수를 수용하는 메서드가 없는 함수에 `missing` 값을 전달하면 [`MethodError`](@ref)가 발생하며, 이는 다른 유형과 마찬가지입니다.

`missing` 값을 전파하지 않는 함수는 [Missings.jl](https://github.com/JuliaData/Missings.jl) 패키지에서 제공하는 `passmissing` 함수를 사용하여 전파하도록 만들 수 있습니다. 예를 들어, `f(x)`는 `passmissing(f)(x)`로 변환됩니다.

## Equality and Comparison Operators

표준 동등성 및 비교 연산자는 위에 제시된 전파 규칙을 따릅니다: 피연산자 중 하나라도 `missing`인 경우 결과는 `missing`입니다. 다음은 몇 가지 예입니다:

```jldoctest
julia> missing == 1
missing

julia> missing == missing
missing

julia> missing < 1
missing

julia> 2 >= missing
missing
```

특히, `missing == missing`는 `missing`을 반환하므로, `==`를 사용하여 값이 누락되었는지 테스트할 수 없습니다. `x`가 `missing`인지 테스트하려면 [`ismissing(x)`](@ref)를 사용하세요.

특별 비교 연산자 [`isequal`](@ref) 및 [`===`](@ref)는 전파 규칙의 예외입니다. 이들은 항상 `Bool` 값을 반환하며, `missing` 값이 존재하더라도 `missing`을 `missing`과 같다고 간주하고 다른 모든 값과는 다르다고 간주합니다. 따라서 이들은 값이 `missing`인지 테스트하는 데 사용할 수 있습니다:

```jldoctest
julia> missing === 1
false

julia> isequal(missing, 1)
false

julia> missing === missing
true

julia> isequal(missing, missing)
true
```

[`isless`](@ref) 연산자는 또 다른 예외입니다: `missing`은 다른 모든 값보다 큰 것으로 간주됩니다. 이 연산자는 [`sort!`](@ref)에 의해 사용되며, 따라서 `missing` 값은 모든 다른 값 뒤에 배치됩니다:

```jldoctest
julia> isless(1, missing)
true

julia> isless(missing, Inf)
false

julia> isless(missing, missing)
false
```

## Logical operators

논리적(또는 불리언) 연산자 [`|`](@ref), [`&`](@ref) 및 [`xor`](@ref)는 논리적으로 필요할 때만 `missing` 값을 전파하기 때문에 또 다른 특별한 경우입니다. 이러한 연산자에 대해 결과가 불확실한지 여부는 특정 연산에 따라 다릅니다. 이는 [*three-valued logic*](https://en.wikipedia.org/wiki/Three-valued_logic)의 잘 확립된 규칙을 따르며, 이는 예를 들어 SQL의 `NULL` 및 R의 `NA`에 의해 구현됩니다. 이 추상적인 정의는 구체적인 예를 통해 가장 잘 설명되는 상대적으로 자연스러운 행동에 해당합니다.

이 원리를 논리 "또는" 연산자 [`|`](@ref)로 설명해 보겠습니다. 불리언 논리의 규칙에 따르면, 피연산자 중 하나가 `참`이면 다른 피연산자의 값은 결과에 영향을 미치지 않으며, 결과는 항상 `참`이 됩니다:

```jldoctest
julia> true | true
true

julia> true | false
true

julia> false | true
true
```

이 관찰을 바탕으로, 만약 두 피연산자 중 하나가 `true`이고 다른 하나가 `missing`이라면, 우리는 실제 피연산자 중 하나의 값에 대한 불확실성에도 불구하고 결과가 `true`임을 알 수 있습니다. 만약 두 번째 피연산자의 실제 값을 관찰할 수 있었다면, 그것은 오직 `true` 또는 `false`일 수 있으며, 두 경우 모두 결과는 `true`가 될 것입니다. 따라서 이 특정 경우에서, 결측값은 *전파되지* 않습니다:

```jldoctest
julia> true | missing
true

julia> missing | true
true
```

반대로, 만약 피연산자 중 하나가 `false`라면, 결과는 다른 피연산자의 값에 따라 `true` 또는 `false`가 될 수 있습니다. 따라서 그 피연산자가 `missing`인 경우, 결과도 `missing`이어야 합니다:

```jldoctest
julia> false | true
true

julia> true | false
true

julia> false | false
false

julia> false | missing
missing

julia> missing | false
missing
```

논리 "and" 연산자 [`&`](@ref)의 동작은 `|` 연산자와 유사하지만, 한 피연산자가 `false`일 때 결측값이 전파되지 않는다는 차이가 있습니다. 예를 들어, 첫 번째 피연산자가 그런 경우:

```jldoctest
julia> false & false
false

julia> false & true
false

julia> false & missing
false
```

반면, 결측값은 피연산자 중 하나가 `true`일 때 전파됩니다. 예를 들어 첫 번째 피연산자입니다:

```jldoctest
julia> true & true
true

julia> true & false
false

julia> true & missing
missing
```

마침내 "배타적 또는" 논리 연산자 [`xor`](@ref)는 항상 `missing` 값을 전파합니다. 두 피연산자가 항상 결과에 영향을 미치기 때문입니다. 또한 부정 연산자 [`!`](@ref)는 피연산자가 `missing`일 때 `missing`을 반환한다는 점에 유의하세요. 다른 단항 연산자와 마찬가지입니다.

## Control Flow and Short-Circuiting Operators

제어 흐름 연산자에는 [`if`](@ref), [`while`](@ref) 및 [ternary operator](@ref man-conditional-evaluation) `x ? y : z`가 포함되며, 이는 누락된 값을 허용하지 않습니다. 이는 우리가 실제 값이 `true`인지 `false`인지 관찰할 수 없기 때문에 발생하는 불확실성 때문입니다. 이는 프로그램이 어떻게 동작해야 하는지 알 수 없음을 의미합니다. 이 경우, 이 맥락에서 `missing` 값이 발견되면 즉시 [`TypeError`](@ref)가 발생합니다:

```jldoctest
julia> if missing
           println("here")
       end
ERROR: TypeError: non-boolean (Missing) used in boolean context
```

같은 이유로, 위에 제시된 논리 연산자와는 달리, 단락 평가 부울 연산자 [`&&`](@ref)와 [`||`](@ref)는 피연산자의 값이 다음 피연산자가 평가되는지 여부를 결정하는 상황에서 `missing` 값을 허용하지 않습니다. 예를 들어:

```jldoctest
julia> missing || false
ERROR: TypeError: non-boolean (Missing) used in boolean context

julia> missing && false
ERROR: TypeError: non-boolean (Missing) used in boolean context

julia> true && missing && false
ERROR: TypeError: non-boolean (Missing) used in boolean context
```

대조적으로, `missing` 값 없이 결과를 결정할 수 있을 때는 오류가 발생하지 않습니다. 이는 코드가 `missing` 피연산자를 평가하기 전에 단축 평가(short-circuit)될 때와 `missing` 피연산자가 마지막일 때의 경우입니다:

```jldoctest
julia> true && missing
missing

julia> false && missing
false
```

## Arrays With Missing Values

결측값이 포함된 배열은 다른 배열처럼 생성할 수 있습니다:

```jldoctest
julia> [1, missing]
2-element Vector{Union{Missing, Int64}}:
 1
  missing
```

이 예에서 보여주듯이, 이러한 배열의 요소 유형은 `Union{Missing, T}`이며, 여기서 `T`는 누락되지 않은 값의 유형입니다. 이는 배열 항목이 `T` 유형(여기서는 `Int64`) 또는 `Missing` 유형일 수 있음을 반영합니다. 이러한 종류의 배열은 실제 값을 보유하는 `Array{T}`와 항목의 유형(즉, 누락되었는지 또는 `T`인지)을 나타내는 `Array{UInt8}`를 결합하여 효율적인 메모리 저장소를 사용합니다.

누락된 값을 허용하는 배열은 표준 구문으로 구성할 수 있습니다. `Array{Union{Missing, T}}(missing, dims)`를 사용하여 누락된 값으로 채워진 배열을 생성합니다:

```jldoctest
julia> Array{Union{Missing, String}}(missing, 2, 3)
2×3 Matrix{Union{Missing, String}}:
 missing  missing  missing
 missing  missing  missing
```

!!! note
    `undef` 또는 `similar`를 사용하면 현재 `missing`으로 채워진 배열을 얻을 수 있지만, 이는 그러한 배열을 얻는 올바른 방법이 아닙니다. 대신 위에 표시된 대로 `missing` 생성자를 사용하십시오.


An array with element type allowing `missing` entries (e.g. `Vector{Union{Missing, T}}`) which does not contain any `missing` entries can be converted to an array type that does not allow for `missing` entries (e.g. `Vector{T}`) using [`convert`](@ref). If the array contains `missing` values, a `MethodError` is thrown during conversion:

```jldoctest
julia> x = Union{Missing, String}["a", "b"]
2-element Vector{Union{Missing, String}}:
 "a"
 "b"

julia> convert(Array{String}, x)
2-element Vector{String}:
 "a"
 "b"

julia> y = Union{Missing, String}[missing, "b"]
2-element Vector{Union{Missing, String}}:
 missing
 "b"

julia> convert(Array{String}, y)
ERROR: MethodError: Cannot `convert` an object of type Missing to an object of type String
```

## Skipping Missing Values

`missing` 값은 표준 수학 연산자와 함께 전파되므로, 축소 함수는 누락된 값이 포함된 배열에서 호출될 때 `missing`을 반환합니다:

```jldoctest
julia> sum([1, missing])
missing
```

이 상황에서는 [`skipmissing`](@ref) 함수를 사용하여 누락된 값을 건너뜁니다:

```jldoctest
julia> sum(skipmissing([1, missing]))
1
```

이 편리한 함수는 `missing` 값을 효율적으로 필터링하는 반복자를 반환합니다. 따라서 반복자를 지원하는 모든 함수와 함께 사용할 수 있습니다:

```jldoctest skipmissing
julia> x = skipmissing([3, missing, 2, 1])
skipmissing(Union{Missing, Int64}[3, missing, 2, 1])

julia> maximum(x)
3

julia> sum(x)
6

julia> mapreduce(sqrt, +, x)
4.146264369941973
```

`skipmissing`를 배열에 호출하여 생성된 객체는 부모 배열의 인덱스를 사용하여 인덱싱할 수 있습니다. 누락된 값에 해당하는 인덱스는 이러한 객체에 대해 유효하지 않으며, 이를 사용하려고 하면 오류가 발생합니다(이들은 `keys` 및 `eachindex`에 의해 건너뛰어집니다):

```jldoctest skipmissing
julia> x[1]
3

julia> x[2]
ERROR: MissingException: the value at index (2,) is missing
[...]
```

이것은 인덱스에서 작동하는 함수가 `skipmissing`과 결합하여 작동할 수 있도록 합니다. 이는 검색 및 찾기 함수에 특히 해당됩니다. 이러한 함수는 `skipmissing`에 의해 반환된 객체에 대해 유효한 인덱스를 반환하며, 또한 *부모 배열*에서 일치하는 항목의 인덱스이기도 합니다:

```jldoctest skipmissing
julia> findall(==(1), x)
1-element Vector{Int64}:
 4

julia> findfirst(!iszero, x)
1

julia> argmax(x)
1
```

[`collect`](@ref)에서 `missing`이 아닌 값을 추출하고 배열에 저장하세요:

```jldoctest skipmissing
julia> collect(x)
3-element Vector{Int64}:
 3
 2
 1
```

## Logical Operations on Arrays

위에서 설명한 논리 연산자에 대한 삼값 논리는 배열에 적용되는 논리 함수에서도 사용됩니다. 따라서 [`==`](@ref) 연산자를 사용한 배열 동등성 테스트는 `missing` 항목의 실제 값을 알지 못할 경우 결과를 결정할 수 없는 경우 `missing`을 반환합니다. 실제로 이는 비교된 배열의 모든 비어 있지 않은 값이 같지만 하나 또는 두 개의 배열에 비어 있는 값이 포함되어 있는 경우(다른 위치에 있을 수 있음) `missing`이 반환됨을 의미합니다.

```jldoctest
julia> [1, missing] == [2, missing]
false

julia> [1, missing] == [1, missing]
missing

julia> [1, 2, missing] == [1, missing, 2]
missing
```

단일 값의 경우, [`isequal`](@ref)를 사용하여 `missing` 값을 다른 `missing` 값과 동일하게 처리하되, 비어 있지 않은 값과는 다르게 처리합니다:

```jldoctest
julia> isequal([1, missing], [1, missing])
true

julia> isequal([1, 2, missing], [1, missing, 2])
false
```

함수 [`any`](@ref) 및 [`all`](@ref)는 삼값 논리의 규칙을 따릅니다. 따라서 결과를 결정할 수 없을 때 `missing`을 반환합니다:

```jldoctest
julia> all([true, missing])
missing

julia> all([false, missing])
false

julia> any([true, missing])
true

julia> any([false, missing])
missing
```
