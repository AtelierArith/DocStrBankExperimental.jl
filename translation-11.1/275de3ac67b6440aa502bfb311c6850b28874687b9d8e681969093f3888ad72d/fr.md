```
LibGit2.push_head!(w::GitRevWalker)
```

Poussez le commit HEAD et ses ancêtres sur le [`GitRevWalker`](@ref) `w`. Cela garantit que HEAD et tous ses commits ancêtres seront rencontrés lors de la marche.
