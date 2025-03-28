```
llvmcall(fun_ir::String, returntype, Tuple{argtype1, ...}, argvalue1, ...)
llvmcall((mod_ir::String, entry_fn::String), returntype, Tuple{argtype1, ...}, argvalue1, ...)
llvmcall((mod_bc::Vector{UInt8}, entry_fn::String), returntype, Tuple{argtype1, ...}, argvalue1, ...)
```

Rufen Sie den LLVM-Code auf, der im ersten Argument angegeben ist. Es gibt mehrere Möglichkeiten, dieses erste Argument anzugeben:

  * als Literalzeichenfolge, die IR auf Funktionsebene darstellt (ähnlich einem LLVM `define`-Block), wobei die Argumente als aufeinanderfolgende unbenannte SSA-Variablen (%0, %1 usw.) verfügbar sind;
  * als 2-Elemente-Tupel, das eine Zeichenfolge von Modul-IR und eine Zeichenfolge enthält, die den Namen der aufzurufenden Einstiegspunktfunktion darstellt;
  * als 2-Elemente-Tupel, jedoch mit dem Modul, das als `Vector{UInt8}` mit Bitcode bereitgestellt wird.

Beachten Sie, dass im Gegensatz zu `ccall` die Argumenttypen als Tupeltyp angegeben werden müssen und nicht als Tupel von Typen. Alle Typen sowie der LLVM-Code sollten als Literale und nicht als Variablen oder Ausdrücke angegeben werden (es kann erforderlich sein, `@eval` zu verwenden, um diese Literale zu generieren).

[Opake Zeiger](https://llvm.org/docs/OpaquePointers.html) (geschrieben als `ptr`) sind im LLVM-Code nicht erlaubt.

Siehe [`test/llvmcall.jl`](https://github.com/JuliaLang/julia/blob/v1.11.4/test/llvmcall.jl) für Anwendungsbeispiele.
