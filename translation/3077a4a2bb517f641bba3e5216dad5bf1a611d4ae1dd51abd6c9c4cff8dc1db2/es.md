```
@githash_str -> AbstractGitHash
```

Construye un objeto de hash git a partir de la cadena dada, devolviendo un `GitShortHash` si la cadena es más corta que 40 dígitos hexadecimales, de lo contrario un `GitHash`.

# Ejemplos

```jldoctest
julia> LibGit2.githash"d114feb74ce633"
GitShortHash("d114feb74ce633")

julia> LibGit2.githash"d114feb74ce63307afe878a5228ad014e0289a85"
GitHash("d114feb74ce63307afe878a5228ad014e0289a85")
```
