```
;
```

`;`는 많은 C 계열 언어에서와 마찬가지로 Julia에서 이전 문장의 끝을 구분하는 역할을 합니다.

`;`는 줄 끝에 필요하지 않지만, 한 줄에서 문장을 구분하거나 문장을 하나의 표현식으로 결합하는 데 사용할 수 있습니다.

REPL에서 줄 끝에 `;`를 추가하면 해당 표현식의 결과 출력이 억제됩니다.

함수 선언에서, 그리고 선택적으로 호출에서, `;`는 일반 인수를 키워드와 구분합니다.

배열 리터럴에서 세미콜론으로 구분된 인수는 그 내용을 함께 연결합니다. 단일 `;`로 만들어진 구분자는 수직으로 연결(즉, 첫 번째 차원에 따라)하고, `;;`는 수평으로 연결(두 번째 차원), `;;;`는 세 번째 차원에 따라 연결하는 등의 방식으로 작동합니다. 이러한 구분자는 대괄호의 마지막 위치에서도 사용되어 길이가 1인 후행 차원을 추가할 수 있습니다.

괄호 안의 첫 번째 위치에 있는 `;`는 명명된 튜플을 구성하는 데 사용할 수 있습니다. 할당의 왼쪽에서 동일한 `(; ...)` 구문은 속성 구조 분해를 허용합니다.

표준 REPL에서 빈 줄에 `;`를 입력하면 셸 모드로 전환됩니다.

# 예제

```jldoctest
julia> function foo()
           x = "Hello, "; x *= "World!"
           return x
       end
foo (generic function with 1 method)

julia> bar() = (x = "Hello, Mars!"; return x)
bar (generic function with 1 method)

julia> foo();

julia> bar()
"Hello, Mars!"

julia> function plot(x, y; style="solid", width=1, color="black")
           ###
       end

julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> [1; 3;; 2; 4;;; 10*A]
2×2×2 Array{Int64, 3}:
[:, :, 1] =
 1  2
 3  4

[:, :, 2] =
 10  20
 30  40

julia> [2; 3;;;]
2×1×1 Array{Int64, 3}:
[:, :, 1] =
 2
 3

julia> nt = (; x=1) # ; 또는 후행 쉼표 없이 이 경우 x에 할당됩니다.
(x = 1,)

julia> key = :a; c = 3;

julia> nt2 = (; key => 1, b=2, c, nt.x)
(a = 1, b = 2, c = 3, x = 1)

julia> (; b, x) = nt2; # 속성 구조 분해를 사용하여 변수 b와 x를 설정합니다.

julia> b, x
(2, 1)

julia> ; # ;를 입력하면 프롬프트가 (제자리에서) shell>로 변경됩니다.
shell> echo hello
hello
```
