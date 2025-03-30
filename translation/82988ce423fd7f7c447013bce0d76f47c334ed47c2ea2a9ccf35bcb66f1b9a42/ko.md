```
@macroexpand [mod,] ex
```

모든 매크로가 제거된 동등한 표현식을 반환합니다(확장됨). 두 개의 인수가 제공되면 첫 번째는 평가할 모듈입니다.

`@macroexpand`와 [`macroexpand`](@ref) 사이에는 차이가 있습니다.

  * [`macroexpand`](@ref)는 키워드 인수 `recursive`를 사용하지만, `@macroexpand`는 항상 재귀적입니다. 비재귀 매크로 버전은 [`@macroexpand1`](@ref)를 참조하십시오.
  * [`macroexpand`](@ref)는 명시적인 `module` 인수를 가지지만, `@macroexpand`는 항상 호출된 모듈에 대해 확장됩니다.

다음 예제에서 가장 잘 볼 수 있습니다:

```julia-repl
julia> module M
           macro m()
               1
           end
           function f()
               (@macroexpand(@m),
                macroexpand(M, :(@m)),
                macroexpand(Main, :(@m))
               )
           end
       end
M

julia> macro m()
           2
       end
@m (매크로가 1개의 메서드를 가짐)

julia> M.f()
(1, 1, 2)
```

`@macroexpand`를 사용하면 표현식이 코드에서 `@macroexpand`가 나타나는 위치(예제의 모듈 `M`)에서 확장됩니다. `macroexpand`를 사용하면 표현식이 첫 번째 인수로 주어진 모듈에서 확장됩니다.

!!! compat "Julia 1.11"
    두 개의 인수 형식은 최소한 Julia 1.11이 필요합니다.

