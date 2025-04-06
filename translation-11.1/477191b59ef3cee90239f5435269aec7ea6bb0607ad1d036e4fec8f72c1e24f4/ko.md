```
macroexpand(m::Module, x; recursive=true)
```

표현식 `x`를 가져와서 모듈 `m`에서 실행하기 위해 모든 매크로가 제거된(확장된) 동등한 표현식을 반환합니다. `recursive` 키워드는 중첩된 매크로의 더 깊은 수준도 확장할지 여부를 제어합니다. 아래 예제에서 설명됩니다:

```julia-repl
julia> module M
           macro m1()
               42
           end
           macro m2()
               :(@m1())
           end
       end
M

julia> macroexpand(M, :(@m2()), recursive=true)
42

julia> macroexpand(M, :(@m2()), recursive=false)
:(#= REPL[16]:6 =# M.@m1)
```
