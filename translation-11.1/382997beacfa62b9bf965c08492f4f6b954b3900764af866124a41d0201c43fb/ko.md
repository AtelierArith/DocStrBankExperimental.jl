```
Base.@assume_effects 설정... [ex]
```

컴파일러의 효과 모델링을 재정의합니다. 이 매크로는 여러 맥락에서 사용할 수 있습니다:

1. 메서드 정의 직전에, 적용된 메서드의 전체 효과 모델링을 재정의합니다.
2. 인수가 없는 함수 본문 내에서, 포함된 메서드의 전체 효과 모델링을 재정의합니다.
3. 코드 블록에 적용하여, 적용된 코드 블록의 로컬 효과 모델링을 재정의합니다.

# 예제

```jldoctest
julia> Base.@assume_effects :terminates_locally function fact(x)
           # 사용 1:
           # 이 :terminates_locally는 `fact`가 상수 접기(constant-folding)될 수 있도록 허용합니다.
           res = 1
           0 ≤ x < 20 || error("잘못된 팩토리얼")
           while x > 1
               res *= x
               x -= 1
           end
           return res
       end
fact (generic function with 1 method)

julia> code_typed() do
           fact(12)
       end |> only
CodeInfo(
1 ─     return 479001600
) => Int64

julia> code_typed() do
           map((2,3,4)) do x
               # 사용 2:
               # 이 :terminates_locally는 이 익명 함수가 상수 접기될 수 있도록 허용합니다.
               Base.@assume_effects :terminates_locally
               res = 1
               0 ≤ x < 20 || error("잘못된 팩토리얼")
               while x > 1
                   res *= x
                   x -= 1
               end
               return res
           end
       end |> only
CodeInfo(
1 ─     return (2, 6, 24)
) => Tuple{Int64, Int64, Int64}

julia> code_typed() do
           map((2,3,4)) do x
               res = 1
               0 ≤ x < 20 || error("잘못된 팩토리얼")
               # 사용 3:
               # 이 :terminates_locally 주석이 있으면 컴파일러가
               # 이 `while` 블록 내에서 `:terminates` 효과를 오염시키지 않도록 하여
               # 부모 익명 함수가 상수 접기될 수 있도록 허용합니다.
               Base.@assume_effects :terminates_locally while x > 1
                   res *= x
                   x -= 1
               end
               return res
           end
       end |> only
CodeInfo(
1 ─     return (2, 6, 24)
) => Tuple{Int64, Int64, Int64}
```

!!! compat "Julia 1.8"
    `Base.@assume_effects`를 사용하려면 Julia 버전 1.8이 필요합니다.


!!! compat "Julia 1.10"
    함수 본문 내에서의 사용은 최소한 Julia 1.10이 필요합니다.


!!! compat "Julia 1.11"
    코드 블록 주석은 최소한 Julia 1.11이 필요합니다.


!!! warning
    이 매크로를 부적절하게 사용하면 정의되지 않은 동작(충돌, 잘못된 답변 또는 추적하기 어려운 기타 버그 포함)을 초래할 수 있습니다. 주의해서 사용하고 절대적으로 필요한 경우에만 마지막 수단으로 사용하십시오. 그러한 경우에도 효과 주장을 최소화하기 위해 가능한 모든 조치를 취해야 합니다(예: `:nothrow`가 충분했을 경우 `:total`을 사용하지 마십시오).


일반적으로 각 `setting` 값은 함수의 동작에 대한 주장을 하며, 컴파일러가 이 동작이 실제로 참인지 증명할 필요는 없습니다. 이러한 주장은 모든 세계 연령에 대해 이루어집니다. 따라서 나중에 가정이 무효화될 수 있는 일반 함수를 사용하는 것을 제한하는 것이 좋습니다(이는 정의되지 않은 동작을 초래할 수 있습니다).

다음 `setting`이 지원됩니다.

  * `:consistent`
  * `:effect_free`
  * `:nothrow`
  * `:terminates_globally`
  * `:terminates_locally`
  * `:notaskstate`
  * `:inaccessiblememonly`
  * `:noub`
  * `:noub_if_noinbounds`
  * `:nortcall`
  * `:foldable`
  * `:removable`
  * `:total`

# 확장 도움말

---

## `:consistent`

`:consistent` 설정은 동등(`===`)한 입력에 대해 다음을 주장합니다:

  * 종료 방식(반환 값, 예외, 비종료)은 항상 동일합니다.
  * 메서드가 반환하는 경우 결과는 항상 동등합니다.

!!! note
    이는 특히 메서드가 새로 할당된 가변 객체를 반환해서는 안 됨을 의미합니다. 가변 객체의 여러 할당(내용이 동일하더라도)은 동등하지 않습니다.


!!! note
    `:consistent`-cy 주장은 세계 연령별로 이루어집니다. 보다 공식적으로, $fᵢ$를 세계 연령 $i$에서의 $f$의 평가로 쓰면, 이 설정은 다음을 요구합니다:

    $$
    ∀ i, x, y: x ≡ y → fᵢ(x) ≡ fᵢ(y)
    $$

    그러나 두 세계 연령 $i$, $j$에 대해 $i ≠ j$인 경우, $fᵢ(x) ≢ fⱼ(y)$일 수 있습니다.

    추가적인 의미는 `:consistent` 함수가 반환 값을 힙의 상태나 주어진 세계 연령에 대해 상수적이지 않은 다른 전역 상태에 의존해서는 안 된다는 것입니다.


!!! note
    `:consistent`-cy는 최적화 프로그램이 수행하는 모든 합법적인 재작성(rewrites)을 포함합니다. 예를 들어, 부동 소수점 fastmath 연산은 `:consistent`로 간주되지 않으며, 최적화 프로그램이 이를 재작성하여 출력이 `:consistent`가 되지 않을 수 있습니다. 같은 세계 연령에 대해서도(예: 하나는 인터프리터에서 실행되고 다른 하나는 최적화된 경우).


!!! note
    `:consistent` 함수가 예외를 던져 종료되는 경우, 그 예외 자체는 위에서 지정한 동등성 요구 사항을 충족할 필요는 없습니다.


---

## `:effect_free`

`:effect_free` 설정은 메서드가 외부에서 의미적으로 가시적인 부작용이 없음을 주장합니다. 다음은 외부에서 의미적으로 가시적인 부작용의 불완전한 목록입니다:

  * 전역 변수의 값 변경.
  * 힙의 변형(예: 배열 또는 가변 값), 아래에 언급된 경우를 제외하고
  * 메서드 테이블 변경(예: eval 호출을 통해)
  * 파일/네트워크 등 I/O
  * 작업 전환

그러나 다음은 명시적으로 의미적으로 가시적이지 않으며, 관찰 가능할 수 있습니다:

  * 메모리 할당(가변 및 불변 모두)
  * 경과 시간
  * 가비지 수집
  * 메서드의 수명보다 짧은 객체의 힙 변형(즉, 메서드 내에서 할당되고 탈출하지 않음).
  * 반환된 값(외부에서 가시적이지만 부작용이 아님)

여기서의 경험 법칙은 외부에서 가시적인 부작용은 함수가 실행되지 않았을 경우 프로그램의 나머지 실행에 영향을 미치는 모든 것입니다.

!!! note
    `:effect_free` 주장은 메서드 자체와 메서드에 의해 실행되는 모든 코드에 대해 이루어집니다. 이 주장은 모든 세계 연령에 대해 유효해야 하며, 따라서 이 주장의 사용을 제한해야 합니다.


---

## `:nothrow`

`:nothrow` 설정은 이 메서드가 예외를 던지지 않음을 주장합니다(즉, 항상 값을 반환하거나 결코 반환하지 않음).

!!! note
    `:nothrow` 주석이 있는 메서드는 내부적으로 예외 처리를 사용할 수 있지만, 예외가 메서드 자체에서 다시 던져지지 않아야 합니다.


!!! note
    메서드의 실행이 `MethodError` 및 유사한 예외를 발생시킬 수 있는 경우, 해당 메서드는 `:nothrow`로 간주되지 않습니다. 그러나 `StackOverflowError` 또는 `InterruptException`과 같은 환경 의존적인 오류는 이 효과에 의해 모델링되지 않으므로, `StackOverflowError`를 초래할 수 있는 메서드는 반드시 `!:nothrow`일 필요는 없습니다(일반적으로 `!:terminates`여야 합니다).


---

## `:terminates_globally`

`:terminates_globally` 설정은 이 메서드가 결국 종료됨(정상적으로 또는 비정상적으로)을 주장합니다. 즉, 무한 루프에 빠지지 않습니다.

!!! note
    이 `:terminates_globally` 주장은 주석이 달린 메서드에 의해 호출되는 다른 모든 메서드를 포함합니다.


!!! note
    컴파일러는 이 메서드가 상대적으로 *빠르게* 종료될 것이라는 강한 신호로 간주하며, 그렇지 않으면 합법적인 경우 이 메서드를 컴파일 시간에 호출할 수 있습니다. 즉, 기술적으로는 종료되지만 실제로는 종료되지 않는 메서드에 이 설정을 주석으로 다는 것은 좋지 않습니다.


---

## `:terminates_locally`

`:terminates_locally` 설정은 `:terminates_globally`와 유사하지만, 주석이 달린 메서드 내의 구문적 제어 흐름에만 적용됩니다. 따라서 이는 메서드가 종료되지 않는 다른 메서드를 호출할 가능성을 허용하는 훨씬 약한(따라서 더 안전한) 주장입니다.

!!! note
    `:terminates_globally`는 `:terminates_locally`를 포함합니다.


---

## `:notaskstate`

`:notaskstate` 설정은 메서드가 로컬 작업 상태(작업 로컬 저장소, RNG 상태 등)를 사용하거나 수정하지 않음을 주장하며, 따라서 관찰 가능한 결과 없이 작업 간에 안전하게 이동할 수 있습니다.

!!! note
    예외 처리의 구현은 작업 객체에 저장된 상태를 사용합니다. 그러나 현재 이 상태는 `:notaskstate`의 범위 내에 있다고 간주되지 않으며, `:nothrow` 효과를 사용하여 별도로 추적됩니다.


!!! note
    `:notaskstate` 주장은 *현재 실행 중인 작업*의 상태에 관한 것입니다. 현재 실행 중인 작업을 고려하지 않고 다른 수단으로 `Task` 객체에 대한 참조를 얻은 경우, `:notaskstate` 효과는 오염될 필요가 없습니다. 이는 해당 작업 객체가 현재 실행 중인 작업과 `===`인 경우에도 마찬가지입니다.


!!! note
    작업 상태에 대한 접근은 일반적으로 `:effect_free`(작업 상태가 수정되는 경우) 또는 `:consistent`(작업 상태가 결과 계산에 사용되는 경우)와 같은 다른 효과의 오염을 초래합니다. 특히, `:notaskstate`가 아니지만 `:effect_free` 및 `:consistent`인 코드는 여전히 죽은 코드 제거(dead-code-elimination)될 수 있으며, 따라서 `:total`로 승격될 수 있습니다.


---

## `:inaccessiblememonly`

`:inaccessiblememonly` 설정은 메서드가 외부에서 접근 가능한 가변 메모리에 접근하거나 수정하지 않음을 주장합니다. 이는 메서드가 반환 전 다른 메서드나 최상위 실행에서 접근할 수 없는 새로 할당된 객체의 가변 메모리에 접근하거나 수정할 수 있지만, 전역 상태나 인수로 전달된 가변 메모리에 접근하거나 수정할 수 없음을 의미합니다.

!!! note
    아래는 이 가정을 무효화하는 불완전한 예시 목록입니다:

      * 가변 전역 변수에 접근하기 위한 전역 참조 또는 `getglobal` 호출
      * 비상수 전역 변수에 대한 할당을 수행하기 위한 전역 할당 또는 `setglobal!` 호출
      * 전역 가변 변수의 필드를 변경하는 `setfield!` 호출


!!! note
    이 `:inaccessiblememonly` 주장은 주석이 달린 메서드에 의해 호출되는 다른 모든 메서드를 포함합니다.


---

## `:noub`

`:noub` 설정은 메서드가 정의되지 않은 동작을 실행하지 않음을 주장합니다(모든 입력에 대해). 정의되지 않은 동작은 기술적으로 메서드가 다른 효과 주장을 위반하게 만들 수 있지만(`:consistent` 또는 `:effect_free`와 같은), 우리는 이를 모델링하지 않으며 정의되지 않은 동작이 없다고 가정합니다.

---

## `:nortcall`

`:nortcall` 설정은 메서드가 `Core.Compiler.return_type`를 호출하지 않으며, 이 메서드가 호출할 수 있는 다른 모든 메서드도 `Core.Compiler.return_type`를 호출하지 않음을 주장합니다.

!!! note
    정확히 말하자면, 이 주장은 런타임에 `Core.Compiler.return_type` 호출이 이루어지지 않을 때 사용할 수 있습니다. 즉, `Core.Compiler.return_type`의 결과가 컴파일 시간에 정확히 알려져 있고 호출이 최적화 프로그램에 의해 제거되는 경우입니다. 그러나 `Core.Compiler.return_type`의 결과가 컴파일 시간에 접어들어지는지는 컴파일러의 구현에 크게 의존하므로, 해당 메서드가 어떤 형태로든 `Core.Compiler.return_type`를 사용하는 경우 이를 주장하는 것은 일반적으로 위험합니다.


---

## `:foldable`

이 설정은 컴파일 시간에 호출을 상수 접기(constant fold)하기 위해 컴파일러가 보장해야 하는 효과 집합에 대한 편리한 단축키입니다. 현재 다음 `setting`과 동등합니다:

  * `:consistent`
  * `:effect_free`
  * `:terminates_globally`
  * `:noub`
  * `:nortcall`

!!! note
    이 목록에는 특히 `:nothrow`가 포함되어 있지 않습니다. 컴파일러는 여전히 상수 전파를 시도하고 컴파일 시간에 던져진 오류를 기록합니다. 그러나 `:consistent`-cy 요구 사항에 따라, 이러한 주석이 달린 호출은 동일한 인수 값에 대해 일관되게 던져야 합니다.


!!! note
    함수 내의 명시적인 `@inbounds` 주석은 또한 상수 접기를 비활성화하며 `:foldable`에 의해 무시되지 않습니다.


---

## `:removable`

이 설정은 컴파일 시간에 결과가 사용되지 않는 호출을 삭제하기 위해 컴파일러가 보장해야 하는 효과 집합에 대한 편리한 단축키입니다. 현재 다음 `setting`과 동등합니다:

  * `:effect_free`
  * `:nothrow`
  * `:terminates_globally`

---

## `:total`

이 `setting`은 가능한 최대 효과 집합입니다. 현재 다음 다른 `setting`을 포함합니다:

  * `:consistent`
  * `:effect_free`
  * `:nothrow`
  * `:terminates_globally`
  * `:notaskstate`
  * `:inaccessiblememonly`
  * `:noub`
  * `:nortcall`

!!! warning
    `:total`은 매우 강력한 주장이며, 향후 Julia 버전에서 추가적인 의미를 가질 가능성이 높습니다(예: 추가 효과가 추가되고 `:total`의 정의에 포함되는 경우). 따라서 주의해서 사용해야 합니다. 가능할 경우 특정 응용 프로그램에 필요한 최소한의 효과 주장을 사용하는 것이 좋습니다. 많은 수의 효과 재정의가 함수 집합에 적용되는 경우, `:total` 사용보다 사용자 정의 매크로를 사용하는 것이 좋습니다.


---

## 부정된 효과

효과 이름은 `!`로 접두어를 붙여 이전 메타 효과에서 효과를 제거해야 함을 나타낼 수 있습니다. 예를 들어, `:total !:nothrow`는 호출이 일반적으로 전체적이지만, 예외를 던질 수 있음을 나타냅니다.
