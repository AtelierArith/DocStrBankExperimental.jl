```
baremodule
```

`baremodule`는 `using Base` 또는 [`eval`](@ref Main.eval) 및 [`include`](@ref Base.include)의 로컬 정의가 포함되지 않은 모듈을 선언합니다. 여전히 `Core`를 가져옵니다. 다시 말해,

```julia
module Mod

...

end
```

는 다음과 동일합니다.

```julia
baremodule Mod

using Base

eval(x) = Core.eval(Mod, x)
include(p) = Base.include(Mod, p)

...

end
```
