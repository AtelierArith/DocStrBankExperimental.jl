```
copyto!(dest::AbstractMatrix, src::UniformScaling)
```

Copie un [`UniformScaling`](@ref) dans une matrice.

!!! compat "Julia 1.1"
    Dans Julia 1.0, cette méthode ne supportait qu'une matrice de destination carrée. Julia 1.1 a ajouté le support pour une matrice rectangulaire.

