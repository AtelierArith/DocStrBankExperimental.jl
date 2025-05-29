```
TimeEvolution{D, TT, GT} <: PrimitiveBlock{D}
```

TimeEvolution, where GT is block type. input matrix should be hermitian.

!!! note
    `TimeEvolution` contructor check hermicity of the input block by default, but sometimes it can be slow. Turn off the check manually by specifying optional parameter `check_hermicity = false`.

