```
merge!(repo::GitRepo, anns::Vector{GitAnnotated}, fastforward::Bool; kwargs...) -> Bool
```

Fusiona los cambios de los commits anotados (capturados como [`GitAnnotated`](@ref) objetos) `anns` en el HEAD del repositorio `repo`. Si `fastforward` es `true`, *solo* se permite una fusión de avance rápido. En este caso, si ocurren conflictos, la fusión fallará. De lo contrario, si `fastforward` es `false`, la fusión puede producir un archivo de conflicto que el usuario deberá resolver.

Los argumentos de palabra clave son:

  * `merge_opts::MergeOptions = MergeOptions()`: opciones sobre cómo realizar la fusión, incluyendo si se permite el avance rápido. Consulta [`MergeOptions`](@ref) para más información.
  * `checkout_opts::CheckoutOptions = CheckoutOptions()`: opciones sobre cómo realizar el checkout. Consulta [`CheckoutOptions`](@ref) para más información.

`anns` puede referirse a cabezas de ramas remotas o locales. Devuelve `true` si la fusión es exitosa, de lo contrario devuelve `false` (por ejemplo, si no es posible la fusión porque las ramas no tienen un ancestro común).

# Ejemplos

```julia
upst_ann_1 = LibGit2.GitAnnotated(repo, "branch/a")

# fusionar la rama, avance rápido
LibGit2.merge!(repo, [upst_ann_1], true)

# ¡conflictos de fusión!
upst_ann_2 = LibGit2.GitAnnotated(repo, "branch/b")
# fusionar la rama, intentar avanzar rápido
LibGit2.merge!(repo, [upst_ann_2], true) # devolverá false
LibGit2.merge!(repo, [upst_ann_2], false) # devolverá true
```
