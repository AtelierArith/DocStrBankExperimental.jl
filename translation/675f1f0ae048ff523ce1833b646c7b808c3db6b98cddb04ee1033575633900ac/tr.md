```
baremodule
```

`baremodule`, `using Base` veya [`eval`](@ref Main.eval) ve [`include`](@ref Base.include) için yerel tanımlar içermeyen bir modül bildirir. Yine de `Core`'u içe aktarır. Diğer bir deyişle,

```julia
module Mod

...

end
```

şuna eşdeğerdir:

```julia
baremodule Mod

using Base

eval(x) = Core.eval(Mod, x)
include(p) = Base.include(Mod, p)

...

end
```
