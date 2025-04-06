```
AtomicMemory{T} == GenericMemory{:atomic, T, Core.CPU}
```

Vecteur dense de taille fixe [`DenseVector{T}`](@ref DenseVector). L'accès à n'importe quel de ses éléments se fait de manière atomique (avec un ordre `:monotonic`). La définition de n'importe lequel des éléments doit être réalisée en utilisant le macro `@atomic` et en spécifiant explicitement l'ordre.

!!! warning
    Chaque élément est atomique de manière indépendante lorsqu'il est accédé, et ne peut pas être défini de manière non atomique. Actuellement, le macro `@atomic` et l'interface de niveau supérieur n'ont pas été complétés, mais les éléments de base pour une future implémentation sont les intrinsics internes `Core.memoryrefget`, `Core.memoryrefset!`, `Core.memoryref_isassigned`, `Core.memoryrefswap!`, `Core.memoryrefmodify!`, et `Core.memoryrefreplace!`.


Pour plus de détails, voir [Opérations atomiques](@ref man-atomic-operations)

!!! compat "Julia 1.11"
    Ce type nécessite Julia 1.11 ou une version ultérieure.

