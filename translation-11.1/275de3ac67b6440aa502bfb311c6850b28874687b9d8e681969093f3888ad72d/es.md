```
LibGit2.push_head!(w::GitRevWalker)
```

Empuja el commit HEAD y sus ancestros sobre el [`GitRevWalker`](@ref) `w`. Esto asegura que HEAD y todos sus commits ancestros serán encontrados durante la caminata.
