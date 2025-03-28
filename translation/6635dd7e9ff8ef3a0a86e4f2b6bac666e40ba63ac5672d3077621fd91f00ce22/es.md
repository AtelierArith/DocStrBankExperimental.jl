Las operaciones de punteros inseguros son compatibles con la carga y almacenamiento de punteros declarados con el tipo `_Atomic` y `std::atomic` en C11 y C++23 respectivamente. Se puede lanzar un error si no hay soporte para cargar atómicamente el tipo de Julia `T`.

Véase también: [`unsafe_load`](@ref), [`unsafe_modify!`](@ref), [`unsafe_replace!`](@ref), [`unsafe_store!`](@ref), [`unsafe_swap!`](@ref)
