```
setproperty!(value, name::Symbol, x)
setproperty!(value, name::Symbol, x, order::Symbol)
```

`a.b = c` sözdizimi `setproperty!(a, :b, c)` çağrısını yapar. `@atomic order a.b = c` sözdizimi `setproperty!(a, :b, c, :order)` çağrısını yapar ve `@atomic a.b = c` sözdizimi `setproperty!(a, :b, c, :sequentially_consistent)` çağrısını yapar.

!!! compat "Julia 1.8"
    Modüllerde `setproperty!` en az Julia 1.8 gerektirir.


Ayrıca [`setfield!`](@ref Core.setfield!), [`propertynames`](@ref Base.propertynames) ve [`getproperty`](@ref Base.getproperty) ile de bakabilirsiniz.
