```
llvmcall(fun_ir::String, returntype, Tuple{argtype1, ...}, argvalue1, ...)
llvmcall((mod_ir::String, entry_fn::String), returntype, Tuple{argtype1, ...}, argvalue1, ...)
llvmcall((mod_bc::Vector{UInt8}, entry_fn::String), returntype, Tuple{argtype1, ...}, argvalue1, ...)
```

Llama el código LLVM proporcionado en el primer argumento. Hay varias formas de especificar este primer argumento:

  * como una cadena literal, que representa IR a nivel de función (similar a un bloque `define` de LLVM), con argumentos disponibles como variables SSA no nombradas consecutivas (%0, %1, etc.);
  * como una tupla de 2 elementos, que contiene una cadena de IR de módulo y una cadena que representa el nombre de la función de entrada a llamar;
  * como una tupla de 2 elementos, pero con el módulo proporcionado como un `Vector{UInt8}` con código de bits.

Ten en cuenta que, a diferencia de `ccall`, los tipos de argumento deben especificarse como un tipo de tupla, y no como una tupla de tipos. Todos los tipos, así como el código LLVM, deben especificarse como literales, y no como variables o expresiones (puede ser necesario usar `@eval` para generar estos literales).

[Los punteros opacos](https://llvm.org/docs/OpaquePointers.html) (escritos como `ptr`) no están permitidos en el código LLVM.

Consulta [`test/llvmcall.jl`](https://github.com/JuliaLang/julia/blob/v1.11.4/test/llvmcall.jl) para ejemplos de uso.
