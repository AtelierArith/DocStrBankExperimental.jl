```
PipeBuffer(data::AbstractVector{UInt8}=UInt8[]; maxsize::Integer = typemax(Int))
```

Un [`IOBuffer`](@ref) qui permet de lire et effectue des écritures en ajoutant. La recherche et la troncature ne sont pas prises en charge. Voir [`IOBuffer`](@ref) pour les constructeurs disponibles. Si `data` est fourni, crée un `PipeBuffer` pour opérer sur un vecteur de données, en spécifiant éventuellement une taille au-delà de laquelle le tableau sous-jacent ne peut pas être agrandi.
