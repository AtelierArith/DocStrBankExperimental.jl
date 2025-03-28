```
llvmcall(fun_ir::String, returntype, Tuple{argtype1, ...}, argvalue1, ...)
llvmcall((mod_ir::String, entry_fn::String), returntype, Tuple{argtype1, ...}, argvalue1, ...)
llvmcall((mod_bc::Vector{UInt8}, entry_fn::String), returntype, Tuple{argtype1, ...}, argvalue1, ...)
```

Appelez le code LLVM fourni dans le premier argument. Il existe plusieurs façons de spécifier ce premier argument :

  * comme une chaîne littérale, représentant le IR au niveau de la fonction (similaire à un bloc `define` LLVM), avec des arguments disponibles sous forme de variables SSA non nommées (%0, %1, etc.) ;
  * comme un tuple de 2 éléments, contenant une chaîne de IR de module et une chaîne représentant le nom de la fonction d'entrée à appeler ;
  * comme un tuple de 2 éléments, mais avec le module fourni sous forme de `Vector{UInt8}` avec du bitcode.

Notez qu'à la différence de `ccall`, les types d'arguments doivent être spécifiés comme un type de tuple, et non comme un tuple de types. Tous les types, ainsi que le code LLVM, doivent être spécifiés comme des littéraux, et non comme des variables ou des expressions (il peut être nécessaire d'utiliser `@eval` pour générer ces littéraux).

[Les pointeurs opaques](https://llvm.org/docs/OpaquePointers.html) (écrits comme `ptr`) ne sont pas autorisés dans le code LLVM.

Voir [`test/llvmcall.jl`](https://github.com/JuliaLang/julia/blob/v1.11.4/test/llvmcall.jl) pour des exemples d'utilisation.
