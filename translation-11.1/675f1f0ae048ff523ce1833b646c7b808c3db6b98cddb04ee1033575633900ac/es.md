```
baremodule
```

`baremodule` declara un módulo que no contiene `using Base` ni definiciones locales de [`eval`](@ref Main.eval) y [`include`](@ref Base.include). Sin embargo, todavía importa `Core`. En otras palabras,

```julia
module Mod

...

end
```

es equivalente a

```julia
baremodule Mod

using Base

eval(x) = Core.eval(Mod, x)
include(p) = Base.include(Mod, p)

...

end
```
