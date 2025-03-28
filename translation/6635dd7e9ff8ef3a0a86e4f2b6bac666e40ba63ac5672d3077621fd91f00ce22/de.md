Unsichere Zeigeroperationen sind kompatibel mit dem Laden und Speichern von Zeigern, die mit `_Atomic` und `std::atomic` Typ in C11 und C++23 deklariert sind. Ein Fehler kann auftreten, wenn es keine Unterstützung für das atomare Laden des Julia-Typs `T` gibt.

Siehe auch: [`unsafe_load`](@ref), [`unsafe_modify!`](@ref), [`unsafe_replace!`](@ref), [`unsafe_store!`](@ref), [`unsafe_swap!`](@ref)
