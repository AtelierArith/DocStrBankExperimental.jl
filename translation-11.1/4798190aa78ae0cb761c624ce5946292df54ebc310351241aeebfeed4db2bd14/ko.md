```
ENV
```

단일 인스턴스 `EnvDict`에 대한 참조로, 시스템 환경 변수에 대한 사전 인터페이스를 제공합니다.

(Windows에서는 시스템 환경 변수가 대소문자를 구분하지 않으며, `ENV`는 표시, 반복 및 복사를 위해 모든 키를 대문자로 변환합니다. 이식 가능한 코드는 대소문자로 변수를 구분할 수 있는 능력에 의존해서는 안 되며, 겉보기에는 소문자인 변수를 설정하면 대문자 `ENV` 키가 생성될 수 있음을 주의해야 합니다.)

!!! 경고     환경을 변경하는 것은 스레드 안전하지 않습니다.

# 예제

```julia-repl
julia> ENV
Base.EnvDict with "50" entries:
  "SECURITYSESSIONID"            => "123"
  "USER"                         => "username"
  "MallocNanoZone"               => "0"
  ⋮                              => ⋮

julia> ENV["JULIA_EDITOR"] = "vim"
"vim"

julia> ENV["JULIA_EDITOR"]
"vim"
```

또한 참조: [`withenv`](@ref), [`addenv`](@ref).
