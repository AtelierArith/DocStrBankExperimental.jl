```
normalize!(a::AbstractArray, p::Real=2)
```

배열 `a`를 제자리에서 정규화하여 `p`-노름이 1이 되도록 합니다. 즉, `norm(a, p) == 1`입니다. 또한 [`normalize`](@ref) 및 [`norm`](@ref)를 참조하십시오.
