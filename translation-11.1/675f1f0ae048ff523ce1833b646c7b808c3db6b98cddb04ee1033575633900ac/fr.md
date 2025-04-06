```
baremodule
```

`baremodule` déclare un module qui ne contient pas `using Base` ou des définitions locales de [`eval`](@ref Main.eval) et [`include`](@ref Base.include). Il importe néanmoins `Core`. En d'autres termes,

```julia
module Mod

...

end
```

est équivalent à

```julia
baremodule Mod

using Base

eval(x) = Core.eval(Mod, x)
include(p) = Base.include(Mod, p)

...

end
```
