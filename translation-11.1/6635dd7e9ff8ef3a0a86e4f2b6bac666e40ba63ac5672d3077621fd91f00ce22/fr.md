Les opérations de pointeur non sécurisées sont compatibles avec le chargement et le stockage de pointeurs déclarés avec le type `_Atomic` et `std::atomic` en C11 et C++23 respectivement. Une erreur peut être générée s'il n'y a pas de support pour le chargement atomique du type Julia `T`.

Voir aussi : [`unsafe_load`](@ref), [`unsafe_modify!`](@ref), [`unsafe_replace!`](@ref), [`unsafe_store!`](@ref), [`unsafe_swap!`](@ref)
