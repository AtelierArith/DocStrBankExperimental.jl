```
baremodule
```

`baremodule` deklariert ein Modul, das kein `using Base` oder lokale Definitionen von [`eval`](@ref Main.eval) und [`include`](@ref Base.include) enthält. Es importiert jedoch weiterhin `Core`. Mit anderen Worten,

```julia
module Mod

...

end
```

ist äquivalent zu

```julia
baremodule Mod

using Base

eval(x) = Core.eval(Mod, x)
include(p) = Base.include(Mod, p)

...

end
```
