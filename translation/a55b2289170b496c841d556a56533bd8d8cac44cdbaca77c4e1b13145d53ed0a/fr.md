```
LibGit2.push!(w::GitRevWalker, cid::GitHash)
```

Commencez le [`GitRevWalker`](@ref) `walker` au commit `cid`. Cette fonction peut être utilisée pour appliquer une fonction à tous les commits depuis une certaine année, en passant le premier commit de cette année comme `cid` et en passant ensuite le `w` résultant à [`LibGit2.map`](@ref).
