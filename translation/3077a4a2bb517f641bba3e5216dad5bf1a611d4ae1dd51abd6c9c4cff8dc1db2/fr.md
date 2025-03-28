```
@githash_str -> AbstractGitHash
```

Construit un objet de hachage git à partir de la chaîne donnée, retournant un `GitShortHash` si la chaîne est plus courte que 40 chiffres hexadécimaux, sinon un `GitHash`.

# Exemples

```jldoctest
julia> LibGit2.githash"d114feb74ce633"
GitShortHash("d114feb74ce633")

julia> LibGit2.githash"d114feb74ce63307afe878a5228ad014e0289a85"
GitHash("d114feb74ce63307afe878a5228ad014e0289a85")
```
