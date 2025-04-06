```
baremodule
```

`baremodule` 声明一个不包含 `using Base` 或 [`eval`](@ref Main.eval) 和 [`include`](@ref Base.include) 的局部定义的模块。它仍然导入 `Core`。换句话说，

```julia
module Mod

...

end
```

等价于

```julia
baremodule Mod

using Base

eval(x) = Core.eval(Mod, x)
include(p) = Base.include(Mod, p)

...

end
```
