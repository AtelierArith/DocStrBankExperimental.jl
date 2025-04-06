```
eigen!(A; permute, scale, sortby)
eigen!(A, B; sortby)
```

[`eigen`](@ref) ile aynı, ancak bir kopya oluşturmak yerine girdi `A` (ve `B`) üzerine yazarak alan tasarrufu sağlar.
