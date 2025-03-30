# [Single- and multi-dimensional Arrays](@id man-multi-dim-arrays)

줄리아는 대부분의 기술 컴퓨팅 언어와 마찬가지로 일급 배열 구현을 제공합니다. 대부분의 기술 컴퓨팅 언어는 다른 컨테이너를 희생하면서 배열 구현에 많은 주의를 기울입니다. 줄리아는 배열을 특별한 방식으로 취급하지 않습니다. 배열 라이브러리는 거의 완전히 줄리아 자체로 구현되어 있으며, 줄리아로 작성된 다른 코드와 마찬가지로 컴파일러에서 성능을 끌어냅니다. 따라서 [`AbstractArray`](@ref)에서 상속하여 사용자 정의 배열 유형을 정의하는 것도 가능합니다. 사용자 정의 배열 유형 구현에 대한 자세한 내용은 [manual section on the AbstractArray interface](@ref man-interface-array)를 참조하세요.

배열은 다차원 그리드에 저장된 객체의 모음입니다. 0차원 배열은 허용되며, [this FAQ entry](@ref faq-array-0dim)를 참조하십시오. 가장 일반적인 경우, 배열은 [`Any`](@ref) 유형의 객체를 포함할 수 있습니다. 대부분의 계산 목적을 위해, 배열은 [`Float64`](@ref) 또는 [`Int32`](@ref)와 같은 보다 구체적인 유형의 객체를 포함해야 합니다.

일반적으로, 많은 다른 기술 컴퓨팅 언어와 달리, Julia는 성능을 위해 프로그램이 벡터화된 스타일로 작성되기를 기대하지 않습니다. Julia의 컴파일러는 타입 추론을 사용하고 스칼라 배열 인덱싱에 대해 최적화된 코드를 생성하여, 성능을 희생하지 않으면서도 편리하고 읽기 쉬운 스타일로 프로그램을 작성할 수 있게 합니다. 때때로 메모리 사용량도 줄일 수 있습니다.

줄리아에서 함수에 대한 모든 인수는 [passed by sharing](https://en.wikipedia.org/wiki/Evaluation_strategy#Call_by_sharing) (즉, 포인터로) 전달됩니다. 일부 기술 컴퓨팅 언어는 배열을 값으로 전달하는데, 이는 호출자가 값의 우발적인 수정을 방지하지만, 원하지 않는 배열 복사를 피하는 것을 어렵게 만듭니다. 관례적으로, `!`로 끝나는 함수 이름은 하나 이상의 인수의 값을 변형하거나 파괴할 것임을 나타냅니다 (예를 들어, [`sort`](@ref)와 [`sort!`](@ref)를 비교하십시오). 호출자는 변경할 의도가 없는 입력을 수정하지 않도록 명시적인 복사를 만들어야 합니다. 많은 비변형 함수는 입력의 명시적 복사본에서 끝에 `!`가 추가된 동일한 이름의 함수를 호출하여 구현되며, 그 복사본을 반환합니다.

## Basic Functions

| Function               | Description                                                                      |
|:---------------------- |:-------------------------------------------------------------------------------- |
| [`eltype(A)`](@ref)    | the type of the elements contained in `A`                                        |
| [`length(A)`](@ref)    | the number of elements in `A`                                                    |
| [`ndims(A)`](@ref)     | the number of dimensions of `A`                                                  |
| [`size(A)`](@ref)      | a tuple containing the dimensions of `A`                                         |
| [`size(A,n)`](@ref)    | the size of `A` along dimension `n`                                              |
| [`axes(A)`](@ref)      | a tuple containing the valid indices of `A`                                      |
| [`axes(A,n)`](@ref)    | a range expressing the valid indices along dimension `n`                         |
| [`eachindex(A)`](@ref) | an efficient iterator for visiting each position in `A`                          |
| [`stride(A,k)`](@ref)  | the stride (linear index distance between adjacent elements) along dimension `k` |
| [`strides(A)`](@ref)   | a tuple of the strides in each dimension                                         |

## Construction and Initialization

많은 배열을 구성하고 초기화하는 함수가 제공됩니다. 다음 목록에 있는 이러한 함수 중 `dims...` 인수를 사용하는 호출은 단일 튜플의 차원 크기 또는 가변 개수의 인수로 전달된 일련의 차원 크기를 사용할 수 있습니다. 이러한 함수의 대부분은 배열의 요소 유형인 첫 번째 입력 `T`를 허용합니다. 유형 `T`가 생략되면 기본값은 [`Float64`](@ref)이 됩니다.

| Function                           | Description                                                                                                                                                                                                                                  |
|:---------------------------------- |:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [`Array{T}(undef, dims...)`](@ref) | an uninitialized dense [`Array`](@ref)                                                                                                                                                                                                       |
| [`zeros(T, dims...)`](@ref)        | an `Array` of all zeros                                                                                                                                                                                                                      |
| [`ones(T, dims...)`](@ref)         | an `Array` of all ones                                                                                                                                                                                                                       |
| [`trues(dims...)`](@ref)           | a [`BitArray`](@ref) with all values `true`                                                                                                                                                                                                  |
| [`falses(dims...)`](@ref)          | a `BitArray` with all values `false`                                                                                                                                                                                                         |
| [`reshape(A, dims...)`](@ref)      | an array containing the same data as `A`, but with different dimensions                                                                                                                                                                      |
| [`copy(A)`](@ref)                  | copy `A`                                                                                                                                                                                                                                     |
| [`deepcopy(A)`](@ref)              | copy `A`, recursively copying its elements                                                                                                                                                                                                   |
| [`similar(A, T, dims...)`](@ref)   | an uninitialized array of the same type as `A` (dense, sparse, etc.), but with the specified element type and dimensions. The second and third arguments are both optional, defaulting to the element type and dimensions of `A` if omitted. |
| [`reinterpret(T, A)`](@ref)        | an array with the same binary data as `A`, but with element type `T`                                                                                                                                                                         |
| [`rand(T, dims...)`](@ref)         | an `Array` with random, iid [^1] and uniformly distributed values. For floating point types `T`, the values lie in the half-open interval $[0, 1)$.                                                                                          |
| [`randn(T, dims...)`](@ref)        | an `Array` with random, iid and standard normally distributed values                                                                                                                                                                         |
| [`Matrix{T}(I, m, n)`](@ref)       | `m`-by-`n` identity matrix. Requires `using LinearAlgebra` for [`I`](@ref).                                                                                                                                                                  |
| [`range(start, stop, n)`](@ref)    | a range of `n` linearly spaced elements from `start` to `stop`                                                                                                                                                                               |
| [`fill!(A, x)`](@ref)              | fill the array `A` with the value `x`                                                                                                                                                                                                        |
| [`fill(x, dims...)`](@ref)         | an `Array` filled with the value `x`. In particular, `fill(x)` constructs a zero-dimensional `Array` containing `x`.                                                                                                                         |

[^1]: *iid*, independently and identically distributed.

이러한 함수에 차원을 전달하는 다양한 방법을 보려면 다음 예제를 고려하십시오:

```jldoctest
julia> zeros(Int8, 2, 3)
2×3 Matrix{Int8}:
 0  0  0
 0  0  0

julia> zeros(Int8, (2, 3))
2×3 Matrix{Int8}:
 0  0  0
 0  0  0

julia> zeros((2, 3))
2×3 Matrix{Float64}:
 0.0  0.0  0.0
 0.0  0.0  0.0
```

여기서 `(2, 3)`은 [`Tuple`](@ref)이며 첫 번째 인수인 요소 유형은 선택 사항이며 기본값은 `Float64`입니다.

## [Array literals](@id man-array-literals)

Arrays can also be directly constructed with square braces; the syntax `[A, B, C, ...]` creates a one-dimensional array (i.e., a vector) containing the comma-separated arguments as its elements. The element type ([`eltype`](@ref)) of the resulting array is automatically determined by the types of the arguments inside the braces. If all the arguments are the same type, then that is its `eltype`. If they all have a common [promotion type](@ref conversion-and-promotion) then they get converted to that type using [`convert`](@ref) and that type is the array's `eltype`. Otherwise, a heterogeneous array that can hold anything — a `Vector{Any}` — is constructed; this includes the literal `[]` where no arguments are given. [Array literal can be typed](@ref man-array-typed-literal) with the syntax `T[A, B, C, ...]` where `T` is a type.

```jldoctest
julia> [1, 2, 3] # An array of `Int`s
3-element Vector{Int64}:
 1
 2
 3

julia> promote(1, 2.3, 4//5) # This combination of Int, Float64 and Rational promotes to Float64
(1.0, 2.3, 0.8)

julia> [1, 2.3, 4//5] # Thus that's the element type of this Array
3-element Vector{Float64}:
 1.0
 2.3
 0.8

julia> Float32[1, 2.3, 4//5] # Specify element type manually
3-element Vector{Float32}:
 1.0
 2.3
 0.8

julia> []
Any[]
```

### [Concatenation](@id man-array-concatenation)

대괄호 안의 인수가 쉼표 대신 단일 세미콜론(`;`)이나 줄 바꿈으로 구분되면, 그 내용이 *수직으로 연결*되어 함께 결합됩니다.

```jldoctest
julia> [1:2, 4:5] # Has a comma, so no concatenation occurs. The ranges are themselves the elements
2-element Vector{UnitRange{Int64}}:
 1:2
 4:5

julia> [1:2; 4:5]
4-element Vector{Int64}:
 1
 2
 4
 5

julia> [1:2
        4:5
        6]
5-element Vector{Int64}:
 1
 2
 4
 5
 6
```

유사하게, 인수가 탭이나 공백 또는 이중 세미콜론으로 구분되면 그 내용이 *수평으로 연결*됩니다.

```jldoctest
julia> [1:2  4:5  7:8]
2×3 Matrix{Int64}:
 1  4  7
 2  5  8

julia> [[1,2]  [4,5]  [7,8]]
2×3 Matrix{Int64}:
 1  4  7
 2  5  8

julia> [1 2 3] # Numbers can also be horizontally concatenated
1×3 Matrix{Int64}:
 1  2  3

julia> [1;; 2;; 3;; 4]
1×4 Matrix{Int64}:
 1  2  3  4
```

단일 세미콜론(또는 줄 바꿈)과 공백(또는 탭)을 결합하여 수평 및 수직으로 동시에 연결할 수 있습니다.

```jldoctest
julia> [1 2
        3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> [zeros(Int, 2, 2) [1; 2]
        [3 4]            5]
3×3 Matrix{Int64}:
 0  0  1
 0  0  2
 3  4  5

julia> [[1 1]; 2 3; [4 4]]
3×2 Matrix{Int64}:
 1  1
 2  3
 4  4
```

공백(및 탭)은 세미콜론보다 우선 순위가 높아 먼저 수평 연결을 수행한 다음 결과를 연결합니다. 반면에 수평 연결을 위해 이중 세미콜론을 사용하면 수직 연결을 먼저 수행한 후 결과를 수평으로 연결합니다.

```jldoctest
julia> [zeros(Int, 2, 2) ; [3 4] ;; [1; 2] ; 5]
3×3 Matrix{Int64}:
 0  0  1
 0  0  2
 3  4  5

julia> [1:2; 4;; 1; 3:4]
3×2 Matrix{Int64}:
 1  1
 2  3
 4  4
```

`;`와 `;;`가 첫 번째 및 두 번째 차원에서 연결되는 것처럼, 더 많은 세미콜론을 사용하면 이 동일한 일반적인 방식이 확장됩니다. 구분 기호에 있는 세미콜론의 수는 특정 차원을 지정하므로 `;;;`는 세 번째 차원에서 연결되고, `;;;;`는 네 번째 차원에서 연결됩니다. 세미콜론이 적을수록 우선권이 있으므로 일반적으로 낮은 차원이 먼저 연결됩니다.

```jldoctest
julia> [1; 2;; 3; 4;; 5; 6;;;
        7; 8;; 9; 10;; 11; 12]
2×3×2 Array{Int64, 3}:
[:, :, 1] =
 1  3  5
 2  4  6

[:, :, 2] =
 7   9  11
 8  10  12
```

이전과 마찬가지로, 수평 연결을 위한 공백(및 탭)은 세미콜론의 수보다 우선 순위가 높습니다. 따라서 고차원 배열은 먼저 행을 지정하고 그 요소를 배치와 유사한 방식으로 텍스트로 배열하여 작성할 수 있습니다:

```jldoctest
julia> [1 3 5
        2 4 6;;;
        7 9 11
        8 10 12]
2×3×2 Array{Int64, 3}:
[:, :, 1] =
 1  3  5
 2  4  6

[:, :, 2] =
 7   9  11
 8  10  12

julia> [1 2;;; 3 4;;;; 5 6;;; 7 8]
1×2×2×2 Array{Int64, 4}:
[:, :, 1, 1] =
 1  2

[:, :, 2, 1] =
 3  4

[:, :, 1, 2] =
 5  6

[:, :, 2, 2] =
 7  8

julia> [[1 2;;; 3 4];;;; [5 6];;; [7 8]]
1×2×2×2 Array{Int64, 4}:
[:, :, 1, 1] =
 1  2

[:, :, 2, 1] =
 3  4

[:, :, 1, 2] =
 5  6

[:, :, 2, 2] =
 7  8
```

두 번째 차원에서 둘 다 연결을 의미하지만, 공백(또는 탭)과 `;;`는 이중 세미콜론이 단순히 "줄 계속" 문자로 사용되지 않는 한 동일한 배열 표현식에 나타날 수 없습니다. 이는 단일 수평 연결이 여러 줄에 걸쳐 확장될 수 있도록 하며(줄 바꿈이 수직 연결로 해석되지 않도록 함).

```jldoctest
julia> [1 2 ;;
       3 4]
1×4 Matrix{Int64}:
 1  2  3  4
```

종결 세미콜론은 길이 1 차원을 추가하는 데에도 사용될 수 있습니다.

```jldoctest
julia> [1;;]
1×1 Matrix{Int64}:
 1

julia> [2; 3;;;]
2×1×1 Array{Int64, 3}:
[:, :, 1] =
 2
 3
```

보다 일반적으로, 연결은 [`cat`](@ref) 함수로 수행할 수 있습니다. 이러한 구문은 편의 함수인 함수 호출의 약식입니다:

| Syntax                 | Function         | Description                                                                                                |
|:---------------------- |:---------------- |:---------------------------------------------------------------------------------------------------------- |
|                        | [`cat`](@ref)    | concatenate input arrays along dimension(s) `k`                                                            |
| `[A; B; C; ...]`       | [`vcat`](@ref)   | shorthand for `cat(A...; dims=1)`                                                                          |
| `[A B C ...]`          | [`hcat`](@ref)   | shorthand for `cat(A...; dims=2)`                                                                          |
| `[A B; C D; ...]`      | [`hvcat`](@ref)  | simultaneous vertical and horizontal concatenation                                                         |
| `[A; C;; B; D;;; ...]` | [`hvncat`](@ref) | simultaneous n-dimensional concatenation, where number of semicolons indicate the dimension to concatenate |

### [Typed array literals](@id man-array-typed-literal)

특정 요소 유형을 가진 배열은 `T[A, B, C, ...]` 구문을 사용하여 구성할 수 있습니다. 이는 요소 유형 `T`를 가진 1차원 배열을 구성하며, `A`, `B`, `C` 등의 요소로 초기화됩니다. 예를 들어, `Any[x, y, z]`는 어떤 값도 포함할 수 있는 이질적인 배열을 구성합니다.

연결 구문은 결과의 요소 유형을 지정하기 위해 유사하게 유형으로 접두사를 붙일 수 있습니다.

```jldoctest
julia> [[1 2] [3 4]]
1×4 Matrix{Int64}:
 1  2  3  4

julia> Int8[[1 2] [3 4]]
1×4 Matrix{Int8}:
 1  2  3  4
```

## [Comprehensions](@id man-comprehensions)

컴프리헨션은 배열을 구성하는 일반적이고 강력한 방법을 제공합니다. 컴프리헨션 구문은 수학의 집합 구성 표기법과 유사합니다:

```
A = [ F(x, y, ...) for x=rx, y=ry, ... ]
```

이 형식의 의미는 `F(x,y,...)`가 변수 `x`, `y` 등이 주어진 값 목록의 각 값을 취할 때 평가된다는 것입니다. 값은 모든 반복 가능한 객체로 지정할 수 있지만, 일반적으로 `1:n` 또는 `2:(n-1)`와 같은 범위나 `[1.2, 3.4, 5.7]`와 같은 명시적 값 배열이 사용됩니다. 결과는 변수 범위 `rx`, `ry` 등의 차원의 연결로 이루어진 N차원 밀집 배열이며, 각 `F(x,y,...)` 평가 결과는 스칼라를 반환합니다.

다음 예제는 1차원 그리드에서 현재 요소와 그 왼쪽 및 오른쪽 이웃의 가중 평균을 계산합니다. :

```julia-repl
julia> x = rand(8)
8-element Array{Float64,1}:
 0.843025
 0.869052
 0.365105
 0.699456
 0.977653
 0.994953
 0.41084
 0.809411

julia> [ 0.25*x[i-1] + 0.5*x[i] + 0.25*x[i+1] for i=2:length(x)-1 ]
6-element Array{Float64,1}:
 0.736559
 0.57468
 0.685417
 0.912429
 0.8446
 0.656511
```

결과 배열의 유형은 [array literals](@ref man-array-literals)와 같이 계산된 요소의 유형에 따라 달라집니다. 유형을 명시적으로 제어하기 위해, 유형을 이해에 앞서 추가할 수 있습니다. 예를 들어, 단일 정밀도로 결과를 요청하려면 다음과 같이 작성할 수 있습니다:

```julia
Float32[ 0.25*x[i-1] + 0.5*x[i] + 0.25*x[i+1] for i=2:length(x)-1 ]
```

## [Generator Expressions](@id man-generators)

포괄식은 대괄호로 둘러싸지 않고 작성할 수도 있으며, 이를 생성기라고 하는 객체를 생성합니다. 이 객체는 값을 필요에 따라 생성하기 위해 반복할 수 있으며, 미리 배열을 할당하고 저장하는 대신 사용할 수 있습니다 (참조: [Iteration](@ref)). 예를 들어, 다음 표현식은 메모리를 할당하지 않고 일련의 합계를 계산합니다:

```jldoctest
julia> sum(1/n^2 for n=1:1000)
1.6439345666815615
```

여러 차원의 제너레이터 표현식을 인수 목록 안에 작성할 때, 제너레이터와 후속 인수를 구분하기 위해 괄호가 필요합니다:

```julia-repl
julia> map(tuple, 1/(i+j) for i=1:2, j=1:2, [1:4;])
ERROR: syntax: invalid iteration specification
```

모든 쉼표로 구분된 표현식은 `for` 뒤에서 범위로 해석됩니다. 괄호를 추가하면 [`map`](@ref)에 세 번째 인수를 추가할 수 있습니다:

```jldoctest
julia> map(tuple, (1/(i+j) for i=1:2, j=1:2), [1 3; 2 4])
2×2 Matrix{Tuple{Float64, Int64}}:
 (0.5, 1)       (0.333333, 3)
 (0.333333, 2)  (0.25, 4)
```

제너레이터는 내부 함수를 통해 구현됩니다. 언어의 다른 곳에서 사용되는 내부 함수와 마찬가지로, 외부 범위의 변수는 내부 함수에서 "캡처"될 수 있습니다. 예를 들어, `sum(p[i] - q[i] for i=1:n)`는 외부 범위에서 세 개의 변수 `p`, `q` 및 `n`을 캡처합니다. 캡처된 변수는 성능 문제를 일으킬 수 있습니다. [performance tips](@ref man-performance-captured)를 참조하세요.

생성기와 이해를 위한 범위는 여러 개의 `for` 키워드를 작성하여 이전 범위에 의존할 수 있습니다:

```jldoctest
julia> [(i, j) for i=1:3 for j=1:i]
6-element Vector{Tuple{Int64, Int64}}:
 (1, 1)
 (2, 1)
 (2, 2)
 (3, 1)
 (3, 2)
 (3, 3)
```

이러한 경우 결과는 항상 1-d입니다.

생성된 값은 `if` 키워드를 사용하여 필터링할 수 있습니다:

```jldoctest
julia> [(i, j) for i=1:3 for j=1:i if i+j == 4]
2-element Vector{Tuple{Int64, Int64}}:
 (2, 2)
 (3, 1)
```

## [Indexing](@id man-array-indexing)

n차원 배열 `A`에 인덱싱하는 일반 구문은:

```
X = A[I_1, I_2, ..., I_n]
```

각 `I_k`는 스칼라 정수, 정수 배열 또는 기타 [supported index](@ref man-supported-index-types)일 수 있습니다. 여기에는 전체 차원 내의 모든 인덱스를 선택하기 위한 [`Colon`](@ref) (`:`), 연속 또는 간격이 있는 하위 섹션을 선택하기 위한 `a:c` 또는 `a:b:c` 형식의 범위, 그리고 `true` 인덱스에서 요소를 선택하기 위한 부울 배열이 포함됩니다.

모든 인덱스가 스칼라인 경우, 결과 `X`는 배열 `A`의 단일 요소입니다. 그렇지 않으면, `X`는 모든 인덱스의 차원 수의 합과 동일한 차원 수를 가진 배열입니다.

모든 인덱스 `I_k`가 벡터인 경우, `X`의 형태는 `(length(I_1), length(I_2), ..., length(I_n))`가 되며, `X`의 위치 `i_1, i_2, ..., i_n`에는 값 `A[I_1[i_1], I_2[i_2], ..., I_n[i_n]]`이 포함됩니다.

예시:

```jldoctest
julia> A = reshape(collect(1:16), (2, 2, 2, 2))
2×2×2×2 Array{Int64, 4}:
[:, :, 1, 1] =
 1  3
 2  4

[:, :, 2, 1] =
 5  7
 6  8

[:, :, 1, 2] =
  9  11
 10  12

[:, :, 2, 2] =
 13  15
 14  16

julia> A[1, 2, 1, 1] # all scalar indices
3

julia> A[[1, 2], [1], [1, 2], [1]] # all vector indices
2×1×2×1 Array{Int64, 4}:
[:, :, 1, 1] =
 1
 2

[:, :, 2, 1] =
 5
 6

julia> A[[1, 2], [1], [1, 2], 1] # a mix of index types
2×1×2 Array{Int64, 3}:
[:, :, 1] =
 1
 2

[:, :, 2] =
 5
 6
```

결과 배열의 크기가 마지막 두 경우에서 어떻게 다른지 주목하세요.

`I_1`이 2차원 행렬로 변경되면 `X`는 `(size(I_1, 1), size(I_1, 2), length(I_2), ..., length(I_n))` 형태의 `n+1` 차원 배열이 됩니다. 행렬이 차원을 추가합니다.

예시:

```jldoctest
julia> A = reshape(collect(1:16), (2, 2, 2, 2));

julia> A[[1 2; 1 2]]
2×2 Matrix{Int64}:
 1  2
 1  2

julia> A[[1 2; 1 2], 1, 2, 1]
2×2 Matrix{Int64}:
 5  6
 5  6
```

위치 `i_1, i_2, i_3, ..., i_{n+1}`는 `A[I_1[i_1, i_2], I_2[i_3], ..., I_n[i_{n+1}]]`의 값을 포함합니다. 스칼라로 인덱싱된 모든 차원은 제거됩니다. 예를 들어, `J`가 인덱스 배열이라면, `A[2, J, 3]`의 결과는 `size(J)` 크기의 배열입니다. 그 `j`번째 요소는 `A[2, J[j], 3]`로 채워집니다.

이 구문에서 특별한 부분으로, `end` 키워드는 인덱싱 괄호 내에서 각 차원의 마지막 인덱스를 나타내는 데 사용될 수 있으며, 이는 인덱싱되는 가장 안쪽 배열의 크기에 의해 결정됩니다. `end` 키워드 없이 인덱싱 구문은 [`getindex`](@ref) 호출과 동일합니다:

```
X = getindex(A, I_1, I_2, ..., I_n)
```

예시:

```jldoctest
julia> x = reshape(1:16, 4, 4)
4×4 reshape(::UnitRange{Int64}, 4, 4) with eltype Int64:
 1  5   9  13
 2  6  10  14
 3  7  11  15
 4  8  12  16

julia> x[2:3, 2:end-1]
2×2 Matrix{Int64}:
 6  10
 7  11

julia> x[1, [2 3; 4 1]]
2×2 Matrix{Int64}:
  5  9
 13  1
```

## [Indexed Assignment](@id man-indexed-assignment)

n차원 배열 `A`에서 값을 할당하는 일반 구문은 다음과 같습니다:

```
A[I_1, I_2, ..., I_n] = X
```

각 `I_k`는 스칼라 정수, 정수 배열 또는 기타 [supported index](@ref man-supported-index-types)일 수 있습니다. 여기에는 전체 차원 내의 모든 인덱스를 선택하기 위한 [`Colon`](@ref) (`:`), 연속 또는 간격이 있는 하위 섹션을 선택하기 위한 형태 `a:c` 또는 `a:b:c`, 그리고 `true` 인덱스에서 요소를 선택하기 위한 부울 배열이 포함됩니다.

If all indices `I_k` are integers, then the value in location `I_1, I_2, ..., I_n` of `A` is overwritten with the value of `X`, [`convert`](@ref)ing to the [`eltype`](@ref) of `A` if necessary.

If any index `I_k` is itself an array, then the right hand side `X` must also be an array with the same shape as the result of indexing `A[I_1, I_2, ..., I_n]` or a vector with the same number of elements. The value in location `I_1[i_1], I_2[i_2], ..., I_n[i_n]` of `A` is overwritten with the value `X[i_1, i_2, ..., i_n]`, converting if necessary. The element-wise assignment operator `.=` may be used to [broadcast](@ref Broadcasting) `X` across the selected locations:

```
A[I_1, I_2, ..., I_n] .= X
```

[Indexing](@ref man-array-indexing)와 마찬가지로, `end` 키워드는 할당되는 배열의 크기에 의해 결정된 각 차원의 마지막 인덱스를 나타내는 데 사용될 수 있습니다. `end` 키워드 없이 인덱스 할당 구문은 [`setindex!`](@ref)에 대한 호출과 동일합니다:

```
setindex!(A, X, I_1, I_2, ..., I_n)
```

예시:

```jldoctest
julia> x = collect(reshape(1:9, 3, 3))
3×3 Matrix{Int64}:
 1  4  7
 2  5  8
 3  6  9

julia> x[3, 3] = -9;

julia> x[1:2, 1:2] = [-1 -4; -2 -5];

julia> x
3×3 Matrix{Int64}:
 -1  -4   7
 -2  -5   8
  3   6  -9
```

## [Supported index types](@id man-supported-index-types)

표현식 `A[I_1, I_2, ..., I_n]`에서 각 `I_k`는 스칼라 인덱스, 스칼라 인덱스의 배열, 또는 스칼라 인덱스의 배열을 나타내는 객체일 수 있으며, [`to_indices`](@ref)에 의해 그러한 것으로 변환될 수 있습니다:

1. 스칼라 인덱스. 기본적으로 여기에는 다음이 포함됩니다:

      * 비불리언 정수
      * [`CartesianIndex{N}`](@ref)는 여러 차원에 걸쳐 있는 정수의 `N`-튜플처럼 동작합니다 (자세한 내용은 아래를 참조하십시오).
2. 스칼라 인덱스의 배열. 여기에는:

      * 정수의 벡터 및 다차원 배열
      * 빈 배열 `[]`은 요소를 선택하지 않으며, 예를 들어 `A[[]]`와 같이 사용됩니다(이는 `A[]`와 혼동하지 마십시오).
      * `a:c` 또는 `a:b:c`와 같은 범위는 `a`에서 `c`까지(포함) 연속적이거나 간격이 있는 하위 섹션을 선택합니다.
      * `AbstractArray`의 하위 유형인 스칼라 인덱스의 사용자 정의 배열
      * `CartesianIndex{N}`의 배열(자세한 내용은 아래 참조)
3. 객체는 스칼라 인덱스의 배열을 나타내며 [`to_indices`](@ref)에 의해 그러한 것으로 변환될 수 있습니다. 기본적으로 여기에는:

      * [`Colon()`](@ref) (`:`), 이는 전체 차원 내의 모든 인덱스 또는 전체 배열에 걸쳐 있는 모든 인덱스를 나타냅니다.
      * 부울 배열, `true` 인덱스에서 요소를 선택합니다 (자세한 내용은 아래 참조)

일부 예시:

```jldoctest
julia> A = reshape(collect(1:2:18), (3, 3))
3×3 Matrix{Int64}:
 1   7  13
 3   9  15
 5  11  17

julia> A[4]
7

julia> A[[2, 5, 8]]
3-element Vector{Int64}:
  3
  9
 15

julia> A[[1 4; 3 8]]
2×2 Matrix{Int64}:
 1   7
 5  15

julia> A[[]]
Int64[]

julia> A[1:2:5]
3-element Vector{Int64}:
 1
 5
 9

julia> A[2, :]
3-element Vector{Int64}:
  3
  9
 15

julia> A[:, 3]
3-element Vector{Int64}:
 13
 15
 17

julia> A[:, 3:3]
3×1 Matrix{Int64}:
 13
 15
 17
```

### Cartesian indices

특별한 `CartesianIndex{N}` 객체는 여러 차원에 걸쳐 있는 정수의 `N`-튜플처럼 동작하는 스칼라 인덱스를 나타냅니다. 예를 들어:

```jldoctest cartesianindex
julia> A = reshape(1:32, 4, 4, 2);

julia> A[3, 2, 1]
7

julia> A[CartesianIndex(3, 2, 1)] == A[3, 2, 1] == 7
true
```

혼자 고려할 때, 이것은 상대적으로 사소해 보일 수 있습니다; `CartesianIndex`는 단일 다차원 인덱스를 나타내는 하나의 객체로 여러 정수를 모읍니다. 그러나 다른 인덱싱 형태 및 `CartesianIndex`를 생성하는 반복자와 결합하면, 이는 매우 우아하고 효율적인 코드를 생성할 수 있습니다. 아래의 [Iteration](@ref)를 참조하고, 더 고급 예제는 [this blog post on multidimensional algorithms and iteration](https://julialang.org/blog/2016/02/iteration)을 참조하세요.

`CartesianIndex{N}` 배열도 지원됩니다. 이들은 각각 `N` 차원을 가로지르는 스칼라 인덱스의 모음을 나타내며, 때때로 점별 인덱싱이라고 하는 형태의 인덱싱을 가능하게 합니다. 예를 들어, 위에서 `A`의 첫 번째 "페이지"에서 대각선 요소에 접근할 수 있게 해줍니다:

```jldoctest cartesianindex
julia> page = A[:, :, 1]
4×4 Matrix{Int64}:
 1  5   9  13
 2  6  10  14
 3  7  11  15
 4  8  12  16

julia> page[[CartesianIndex(1, 1),
             CartesianIndex(2, 2),
             CartesianIndex(3, 3),
             CartesianIndex(4, 4)]]
4-element Vector{Int64}:
  1
  6
 11
 16
```

이것은 [dot broadcasting](@ref man-vectorized)로 훨씬 더 간단하게 표현될 수 있으며, 이를 일반 정수 인덱스와 결합하여 (A에서 첫 번째 `page`를 별도의 단계로 추출하는 대신) 사용할 수 있습니다. 심지어 `:`와 결합하여 두 페이지에서 두 대각선을 동시에 추출할 수도 있습니다:

```jldoctest cartesianindex
julia> A[CartesianIndex.(axes(A, 1), axes(A, 2)), 1]
4-element Vector{Int64}:
  1
  6
 11
 16

julia> A[CartesianIndex.(axes(A, 1), axes(A, 2)), :]
4×2 Matrix{Int64}:
  1  17
  6  22
 11  27
 16  32
```

!!! warning
    `CartesianIndex`와 `CartesianIndex` 배열은 차원의 마지막 인덱스를 나타내기 위해 `end` 키워드와 호환되지 않습니다. `CartesianIndex` 또는 그 배열이 포함될 수 있는 인덱싱 표현식에서 `end`를 사용하지 마십시오.


### Logical indexing

종종 논리적 인덱싱 또는 논리 마스크를 사용한 인덱싱이라고 불리는 불리언 배열에 의한 인덱싱은 값이 `true`인 인덱스에서 요소를 선택합니다. 불리언 벡터 `B`에 의한 인덱싱은 사실상 [`findall(B)`](@ref)에 의해 반환되는 정수 벡터로 인덱싱하는 것과 동일합니다. 마찬가지로, `N`차원 불리언 배열에 의한 인덱싱은 값이 `true`인 `CartesianIndex{N}`의 벡터로 인덱싱하는 것과 사실상 동일합니다. 논리적 인덱스는 인덱싱하는 차원과 동일한 형태의 배열이어야 하며, 또는 제공된 유일한 인덱스여야 하고 인덱싱하는 배열의 1차원 재구성된 뷰의 형태와 일치해야 합니다. 일반적으로 불리언 배열을 인덱스로 직접 사용하는 것이 [`findall`](@ref)를 먼저 호출하는 것보다 더 효율적입니다.

```jldoctest
julia> x = reshape(1:12, 2, 3, 2)
2×3×2 reshape(::UnitRange{Int64}, 2, 3, 2) with eltype Int64:
[:, :, 1] =
 1  3  5
 2  4  6

[:, :, 2] =
 7   9  11
 8  10  12

julia> x[:, [true false; false true; true false]]
2×3 Matrix{Int64}:
 1  5   9
 2  6  10

julia> mask = map(ispow2, x)
2×3×2 Array{Bool, 3}:
[:, :, 1] =
 1  0  0
 1  1  0

[:, :, 2] =
 0  0  0
 1  0  0

julia> x[mask]
4-element Vector{Int64}:
 1
 2
 4
 8

julia> x[vec(mask)] == x[mask] # we can also index with a single Boolean vector
true
```

### Number of indices

#### Cartesian indexing

`N`-차원 배열에 인덱스를 매기는 일반적인 방법은 정확히 `N`개의 인덱스를 사용하는 것입니다. 각 인덱스는 특정 차원에서의 위치를 선택합니다. 예를 들어, 3차원 배열 `A = rand(4, 3, 2)`에서 `A[2, 3, 1]`은 배열의 첫 번째 "페이지"에서 세 번째 열의 두 번째 행에 있는 숫자를 선택합니다. 이는 종종 *카르테시안 인덱싱*이라고 불립니다.

#### Linear indexing

정확히 하나의 인덱스 `i`가 제공되면, 해당 인덱스는 더 이상 배열의 특정 차원에서 위치를 나타내지 않습니다. 대신, 열 우선 반복 순서를 사용하여 `i`번째 요소를 선택합니다. 이를 *선형 인덱싱*이라고 합니다. 본질적으로 배열을 [`vec`](@ref)로 재구성된 일차원 벡터처럼 취급합니다.

```jldoctest linindexing
julia> A = [2 6; 4 7; 3 1]
3×2 Matrix{Int64}:
 2  6
 4  7
 3  1

julia> A[5]
7

julia> vec(A)[5]
7
```

배열 `A`에 대한 선형 인덱스는 `CartesianIndices(A)[i]`를 사용하여 카르테시안 인덱싱을 위한 `CartesianIndex`로 변환할 수 있습니다 (자세한 내용은 [`CartesianIndices`](@ref) 참조). 또한, `N`개의 카르테시안 인덱스 집합은 `LinearIndices(A)[i_1, i_2, ..., i_N]`를 사용하여 선형 인덱스로 변환할 수 있습니다 (자세한 내용은 [`LinearIndices`](@ref) 참조).

```jldoctest linindexing
julia> CartesianIndices(A)[5]
CartesianIndex(2, 2)

julia> LinearIndices(A)[2, 2]
5
```

이 변환의 성능에는 매우 큰 비대칭이 있다는 점에 유의하는 것이 중요합니다. 선형 인덱스를 카르테시안 인덱스 집합으로 변환하려면 나누기와 나머지를 취해야 하지만, 반대로 가는 것은 단순히 곱하고 더하는 것입니다. 현대 프로세서에서 정수 나누기는 곱셈보다 10-50배 느릴 수 있습니다. 일부 배열 — 예를 들어 [`Array`](@ref) 자체 — 은 선형 메모리 청크를 사용하여 구현되며 구현에서 선형 인덱스를 직접 사용하지만, 다른 배열 — 예를 들어 [`Diagonal`](@ref) — 은 조회를 수행하기 위해 전체 카르테시안 인덱스 집합이 필요합니다 (어떤 것이 어떤 것인지 확인하려면 [`IndexStyle`](@ref)를 참조하십시오).

!!! warning
    배열의 모든 인덱스를 반복할 때, [`eachindex(A)`](@ref)를 반복하는 것이 `1:length(A)`를 반복하는 것보다 낫습니다. 이는 `A`가 `IndexCartesian`인 경우에 더 빠를 뿐만 아니라, [OffsetArrays](https://github.com/JuliaArrays/OffsetArrays.jl)와 같은 사용자 정의 인덱싱을 지원하는 배열도 지원합니다. 값만 필요하다면, 배열을 직접 반복하는 것이 더 좋습니다. 즉, `for a in A`와 같이 사용하면 됩니다.


#### Omitted and extra indices

선형 인덱싱 외에도, `N`차원 배열은 특정 상황에서 `N`개의 인덱스보다 적거나 많은 인덱스로 인덱싱될 수 있습니다.

인덱스는 인덱스가 지정되지 않은 후행 차원의 길이가 모두 1인 경우 생략할 수 있습니다. 다시 말해, 후행 인덱스는 생략할 수 있는 경우는 생략된 인덱스가 유효한 인덱싱 표현에 대해 가질 수 있는 값이 하나뿐일 때만 가능합니다. 예를 들어, 크기가 `(3, 4, 2, 1)`인 4차원 배열은 세 개의 인덱스만으로 인덱싱할 수 있으며, 생략되는 차원(네 번째 차원)의 길이가 1이기 때문입니다. 선형 인덱싱이 이 규칙보다 우선한다는 점에 유의하세요.

```jldoctest
julia> A = reshape(1:24, 3, 4, 2, 1)
3×4×2×1 reshape(::UnitRange{Int64}, 3, 4, 2, 1) with eltype Int64:
[:, :, 1, 1] =
 1  4  7  10
 2  5  8  11
 3  6  9  12

[:, :, 2, 1] =
 13  16  19  22
 14  17  20  23
 15  18  21  24

julia> A[1, 3, 2] # Omits the fourth dimension (length 1)
19

julia> A[1, 3] # Attempts to omit dimensions 3 & 4 (lengths 2 and 1)
ERROR: BoundsError: attempt to access 3×4×2×1 reshape(::UnitRange{Int64}, 3, 4, 2, 1) with eltype Int64 at index [1, 3]

julia> A[19] # Linear indexing
19
```

`A[]`를 사용하여 *모든* 인덱스를 생략할 때, 이 의미는 배열에서 유일한 요소를 검색하고 동시에 요소가 하나만 있었음을 보장하는 간단한 관용구를 제공합니다.

유사하게, 배열의 차원을 초과하는 모든 인덱스가 `1` (또는 더 일반적으로 `axes(A, d)`의 첫 번째이자 유일한 요소인 경우)인 경우 `N` 이상의 인덱스를 제공할 수 있습니다. 이를 통해 벡터를 한 열짜리 행렬처럼 인덱싱할 수 있습니다. 예를 들어:

```jldoctest
julia> A = [8, 6, 7]
3-element Vector{Int64}:
 8
 6
 7

julia> A[2, 1]
6
```

## Iteration

전체 배열을 반복하는 권장 방법은 다음과 같습니다.

```julia
for a in A
    # Do something with the element a
end

for i in eachindex(A)
    # Do something with i and/or A[i]
end
```

첫 번째 구성은 각 요소의 값은 필요하지만 인덱스는 필요하지 않을 때 사용됩니다. 두 번째 구성에서는 `A`가 빠른 선형 인덱싱을 가진 배열 타입이라면 `i`는 `Int`가 되며, 그렇지 않으면 `CartesianIndex`가 됩니다:

```jldoctest
julia> A = rand(4, 3);

julia> B = view(A, 1:3, 2:3);

julia> for i in eachindex(B)
           @show i
       end
i = CartesianIndex(1, 1)
i = CartesianIndex(2, 1)
i = CartesianIndex(3, 1)
i = CartesianIndex(1, 2)
i = CartesianIndex(2, 2)
i = CartesianIndex(3, 2)
```

!!! note
    `for i = 1:length(A)`와 대조적으로, [`eachindex`](@ref)를 사용한 반복은 모든 배열 유형에 대해 효율적인 반복 방법을 제공합니다. 게다가, 이는 [OffsetArrays](https://github.com/JuliaArrays/OffsetArrays.jl)와 같은 사용자 정의 인덱싱을 가진 일반 배열도 지원합니다.


## Array traits

사용자가 정의한 [`AbstractArray`](@ref) 유형을 작성하면, 다음과 같이 빠른 선형 인덱싱을 지정할 수 있습니다.

```julia
Base.IndexStyle(::Type{<:MyArray}) = IndexLinear()
```

이 설정은 `MyArray`에 대한 `eachindex` 반복이 정수를 사용하도록 합니다. 이 특성을 지정하지 않으면 기본값인 `IndexCartesian()`이 사용됩니다.

## [Array and Vectorized Operators and Functions](@id man-array-and-vectorized-operators-and-functions)

다음 연산자는 배열에 대해 지원됩니다:

1. 단항 산술 – `-`, `+`
2. 이진 산술 – `-`, `+`, `*`, `/`, `\`, `^`
3. 비교 – `==`, `!=`, `≈` ([`isapprox`](@ref)), `≉`

수학 및 기타 연산의 편리한 벡터화를 가능하게 하기 위해, Julia [provides the dot syntax](@ref man-vectorized) `f.(args...)`, 예를 들어 `sin.(x)` 또는 `min.(x, y)`는 배열 또는 배열과 스칼라의 혼합에 대한 요소별 연산을 위해 사용됩니다(이는 [Broadcasting](@ref) 연산입니다); 이러한 연산은 다른 점 호출과 결합될 때 "융합"되어 단일 루프로 실행된다는 추가적인 장점이 있습니다, 예를 들어 `sin.(cos.(x))`.

또한, *모든* 이진 연산자는 배열(및 배열과 스칼라의 조합)에 적용할 수 있는 [dot version](@ref man-dot-operators)를 지원합니다. 예를 들어 `z .== sin.(x .* y)`와 같은 [fused broadcasting operations](@ref man-vectorized)에서 사용할 수 있습니다.

`==`와 같은 비교 연산자는 전체 배열에 대해 작동하여 단일 부울 값을 반환합니다. 요소별 비교를 위해서는 `.==`와 같은 점 연산자를 사용하세요. (<와 같은 비교 연산의 경우, 배열에 적용 가능한 것은 오직 요소별 `.<` 버전뿐입니다.)

Also notice the difference between `max.(a,b)`, which [`broadcast`](@ref)s [`max`](@ref) elementwise over `a` and `b`, and [`maximum(a)`](@ref), which finds the largest value within `a`. The same relationship holds for `min.(a, b)` and `minimum(a)`.

## Broadcasting

때때로 서로 다른 크기의 배열에 대해 요소별 이진 연산을 수행하는 것이 유용합니다. 예를 들어, 벡터를 행렬의 각 열에 추가하는 경우가 있습니다. 이를 비효율적으로 수행하는 방법은 벡터를 행렬의 크기로 복제하는 것입니다:

```julia-repl
julia> a = rand(2, 1); A = rand(2, 3);

julia> repeat(a, 1, 3) + A
2×3 Array{Float64,2}:
 1.20813  1.82068  1.25387
 1.56851  1.86401  1.67846
```

이것은 차원이 커질 때 낭비가 되므로 Julia는 [`broadcast`](@ref)를 제공하여 배열 인수의 단일 차원을 다른 배열의 해당 차원과 일치하도록 확장하고 추가 메모리를 사용하지 않으며 주어진 함수를 요소별로 적용합니다:

```julia-repl
julia> broadcast(+, a, A)
2×3 Array{Float64,2}:
 1.20813  1.82068  1.25387
 1.56851  1.86401  1.67846

julia> b = rand(1,2)
1×2 Array{Float64,2}:
 0.867535  0.00457906

julia> broadcast(+, a, b)
2×2 Array{Float64,2}:
 1.71056  0.847604
 1.73659  0.873631
```

[Dotted operators](@ref man-dot-operators)와 같은 `.+` 및 `.*`는 `broadcast` 호출과 동등합니다(단, 이들은 결합되므로 [described above](@ref man-array-and-vectorized-operators-and-functions)). 또한 명시적인 대상을 지정하는 [`broadcast!`](@ref) 함수도 있으며(이는 `.=` 할당을 통해 결합된 방식으로도 접근할 수 있습니다). 사실, `f.(args...)`는 `broadcast(f, args...)`와 동등하여, 모든 함수를 방송하는 편리한 구문을 제공합니다([dot syntax](@ref man-vectorized)). 중첩된 "점 호출" `f.(...)`(여기에는 `.+` 등의 호출이 포함됨) [automatically fuse](@ref man-dot-operators)를 단일 `broadcast` 호출로 결합합니다.

또한, [`broadcast`](@ref)는 배열에 국한되지 않습니다(함수 문서를 참조하십시오); 스칼라, 튜플 및 기타 컬렉션도 처리합니다. 기본적으로 일부 인수 유형만 스칼라로 간주되며, 여기에는 (단, 이에 국한되지 않음) `Number`, `String`, `Symbol`, `Type`, `Function` 및 `missing` 및 `nothing`과 같은 일반적인 싱글톤이 포함됩니다. 다른 모든 인수는 요소별로 반복되거나 인덱싱됩니다.

```jldoctest
julia> convert.(Float32, [1, 2])
2-element Vector{Float32}:
 1.0
 2.0

julia> ceil.(UInt8, [1.2 3.4; 5.6 6.7])
2×2 Matrix{UInt8}:
 0x02  0x04
 0x06  0x07

julia> string.(1:3, ". ", ["First", "Second", "Third"])
3-element Vector{String}:
 "1. First"
 "2. Second"
 "3. Third"
```

가끔 배열과 같은 컨테이너가 일반적으로 브로드캐스트에 참여하는 것을 원치 않을 때, 브로드캐스트가 모든 요소를 반복하는 행동으로부터 "보호"하고 싶을 수 있습니다. 이를 위해 다른 컨테이너(예: 단일 요소 [`Tuple`](@ref)) 안에 배치하면 브로드캐스트는 이를 단일 값으로 취급합니다.

```jldoctest
julia> ([1, 2, 3], [4, 5, 6]) .+ ([1, 2, 3],)
([2, 4, 6], [5, 7, 9])

julia> ([1, 2, 3], [4, 5, 6]) .+ tuple([1, 2, 3])
([2, 4, 6], [5, 7, 9])
```

## Implementation

줄리아에서 기본 배열 유형은 추상 유형 [`AbstractArray{T,N}`](@ref)입니다. 이는 차원 수 `N`과 요소 유형 `T`에 의해 매개변수화됩니다. [`AbstractVector`](@ref) 및 [`AbstractMatrix`](@ref)는 1차원 및 2차원 경우의 별칭입니다. `AbstractArray` 객체에 대한 연산은 기본 저장소와 독립적인 방식으로 더 높은 수준의 연산자 및 함수를 사용하여 정의됩니다. 이러한 연산은 일반적으로 특정 배열 구현에 대한 대체로 올바르게 작동합니다.

`AbstractArray` 타입은 배열과 유사한 모든 것을 포함하며, 그 구현은 전통적인 배열과는 상당히 다를 수 있습니다. 예를 들어, 요소는 저장되는 대신 요청 시 계산될 수 있습니다. 그러나 구체적인 `AbstractArray{T,N}` 타입은 일반적으로 최소한 [`size(A)`](@ref) (정수 튜플 반환), [`getindex(A, i)`](@ref) 및 [`getindex(A, i1, ..., iN)`](@ref getindex)를 구현해야 합니다; 가변 배열은 또한 [`setindex!`](@ref)를 구현해야 합니다. 이러한 연산은 거의 상수 시간 복잡성을 가지는 것이 권장되며, 그렇지 않으면 일부 배열 함수가 예기치 않게 느릴 수 있습니다. 구체적인 타입은 또한 일반적으로 [`similar(A, T=eltype(A), dims=size(A))`](@ref) 메서드를 제공해야 하며, 이는 [`copy`](@ref) 및 기타 위치 변경 작업을 위해 유사한 배열을 할당하는 데 사용됩니다. `AbstractArray{T,N}`가 내부적으로 어떻게 표현되든, `T`는 *정수* 인덱싱(`A[1, ..., 1]`, `A`가 비어 있지 않을 때)으로 반환되는 객체의 타입이며, `N`은 [`size`](@ref)가 반환하는 튜플의 길이여야 합니다. 사용자 정의 `AbstractArray` 구현을 정의하는 방법에 대한 자세한 내용은 [array interface guide in the interfaces chapter](@ref man-interface-array)를 참조하십시오.

`DenseArray`는 `AbstractArray`의 추상 하위 유형으로, 요소가 열 우선 순서로 연속적으로 저장되는 모든 배열을 포함하도록 설계되었습니다(자세한 내용은 [additional notes in Performance Tips](@ref man-performance-column-major) 참조). [`Array`](@ref) 유형은 `DenseArray`의 특정 인스턴스입니다; [`Vector`](@ref) 및 [`Matrix`](@ref)는 1차원 및 2차원 경우에 대한 별칭입니다. `Array`에 대해 구현된 작업은 `AbstractArray`에 대해 요구되는 작업을 넘어서는 것은 매우 적으며, 배열 라이브러리의 대부분은 모든 사용자 정의 배열이 유사하게 동작할 수 있도록 일반적인 방식으로 구현됩니다.

`SubArray`는 원래 배열과 메모리를 공유하여 복사하는 대신 인덱싱을 수행하는 `AbstractArray`의 특수화입니다. `SubArray`는 [`view`](@ref) 함수를 사용하여 생성되며, 이는 [`getindex`](@ref)와 동일한 방식으로 호출됩니다(배열과 일련의 인덱스 인수를 사용). `4d61726b646f776e2e436f64652822222c2022766965772229_40726566`의 결과는 `4d61726b646f776e2e436f64652822222c2022676574696e6465782229_40726566`의 결과와 동일하게 보이지만, 데이터는 제자리에 남아 있습니다. `4d61726b646f776e2e436f64652822222c2022766965772229_40726566`는 입력 인덱스 벡터를 `SubArray` 객체에 저장하며, 이는 나중에 원래 배열을 간접적으로 인덱싱하는 데 사용될 수 있습니다. [`@views`](@ref) 매크로를 표현식이나 코드 블록 앞에 두면, 해당 표현식의 모든 `array[...]` 슬라이스가 `SubArray` 뷰를 생성하도록 변환됩니다.

[`BitArray`](@ref)는 불리언 값을 하나당 하나의 비트를 저장하는 공간 효율적인 "패킹된" 불리언 배열입니다. 이 배열은 `Array{Bool}` 배열(불리언 값당 하나의 바이트를 저장하는 배열)과 유사하게 사용할 수 있으며, 각각 `Array(bitarray)` 및 `BitArray(array)`를 통해 서로 변환할 수 있습니다.

배열은 요소 간의 간격(스트라이드)이 잘 정의된 메모리에 저장되면 "스트라이드"가 있다고 합니다. 지원되는 요소 유형을 가진 스트라이드 배열은 [`pointer`](@ref)와 각 차원의 스트라이드를 단순히 전달하여 BLAS 또는 LAPACK와 같은 외부(비-Julia) 라이브러리에 전달될 수 있습니다. [`stride(A, d)`](@ref)는 차원 `d`를 따라 요소 간의 거리입니다. 예를 들어, `rand(5,7,2)`에 의해 반환된 내장 `Array`는 요소가 열 우선 순서로 연속적으로 배열되어 있습니다. 이는 첫 번째 차원의 스트라이드 — 같은 열의 요소 간의 간격 — 가 `1`임을 의미합니다:

```julia-repl
julia> A = rand(5, 7, 2);

julia> stride(A, 1)
1
```

두 번째 차원의 보폭은 같은 행의 요소들 사이의 간격으로, 단일 열(`5`)에 있는 요소의 수만큼 건너뜁니다. 마찬가지로 두 개의 "페이지" (세 번째 차원 사이)를 건너뛰려면 `5*7 == 35` 요소를 건너뛰어야 합니다. 이 배열의 [`strides`](@ref)는 이 세 숫자의 튜플입니다:

```julia-repl
julia> strides(A)
(1, 5, 35)
```

이 특정 경우에, *메모리*에서 건너뛴 요소의 수는 건너뛴 *선형 인덱스*의 수와 일치합니다. 이는 `Array`(및 기타 `DenseArray` 하위 유형)와 같은 연속 배열에만 해당되며 일반적으로는 사실이 아닙니다. 범위 인덱스를 가진 뷰는 *비연속* 보폭 배열의 좋은 예입니다; `V = @view A[1:3:4, 2:2:6, 2:-1:1]`를 고려해 보십시오. 이 뷰 `V`는 `A`와 동일한 메모리를 참조하지만 일부 요소를 건너뛰고 재배치하고 있습니다. `V`의 첫 번째 차원의 보폭은 `3`입니다. 왜냐하면 원래 배열에서 매 3번째 행만 선택하고 있기 때문입니다:

```julia-repl
julia> V = @view A[1:3:4, 2:2:6, 2:-1:1];

julia> stride(V, 1)
3
```

이 뷰는 원래 `A`에서 다른 모든 열을 선택하고 있으며, 따라서 두 번째 차원에서 인덱스를 이동할 때 두 개의 다섯 요소 열에 해당하는 것을 건너뛰어야 합니다:

```julia-repl
julia> stride(V, 2)
10
```

3차원은 흥미로운데, 그 순서가 반전되어 있기 때문입니다! 따라서 첫 번째 "페이지"에서 두 번째 페이지로 가기 위해서는 메모리에서 *뒤로* 가야 하며, 이 차원에서의 보폭은 음수입니다!

```julia-repl
julia> stride(V, 3)
-35
```

이것은 `V`의 `pointer`가 실제로 `A`의 메모리 블록 중간을 가리키고 있으며, 메모리에서 앞뒤로 요소를 참조한다는 것을 의미합니다. 자신의 스트라이드 배열을 정의하는 방법에 대한 자세한 내용은 [interface guide for strided arrays](@ref man-interface-strided-arrays)를 참조하십시오. [`StridedVector`](@ref) 및 [`StridedMatrix`](@ref)는 스트라이드 배열로 간주되는 많은 내장 배열 유형에 대한 편리한 별칭으로, 포인터와 스트라이드만 사용하여 고도로 조정되고 최적화된 BLAS 및 LAPACK 함수를 호출하는 특수화된 구현을 선택할 수 있도록 합니다.

메모리에서의 오프셋에 관한 것이지 인덱싱에 관한 것이 아니라는 점을 강조할 가치가 있습니다. 선형(단일 인덱스) 인덱싱과 카르테시안(다중 인덱스) 인덱싱 간의 변환을 원하신다면 [`LinearIndices`](@ref) 및 [`CartesianIndices`](@ref)를 참조하세요.
