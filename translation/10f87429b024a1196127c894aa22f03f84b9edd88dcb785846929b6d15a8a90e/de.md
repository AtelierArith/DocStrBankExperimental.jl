# Calling Conventions

Julia verwendet drei Aufrufkonventionen für vier verschiedene Zwecke:

| Name    | Prefix    | Purpose                          |
|:------- |:--------- |:-------------------------------- |
| Native  | `julia_`  | Speed via specialized signatures |
| JL Call | `jlcall_` | Wrapper for generic calls        |
| JL Call | `jl_`     | Builtins                         |
| C ABI   | `jlcapi_` | Wrapper callable from C          |

## Julia Native Calling Convention

Die native Aufrufkonvention ist für schnelle, nicht-generische Aufrufe konzipiert. Sie verwendet normalerweise eine spezialisierte Signatur.

  * LLVM-Geister (Null-Längen-Typen) werden weggelassen.
  * LLVM-Skalaren und -Vektoren werden durch Wertübergabe übergeben.
  * LLVM-Aggregate (Arrays und Strukturen) werden durch Referenz übergeben.

Ein kleiner Rückgabewert wird als LLVM-Rückgabewert zurückgegeben. Ein großer Rückgabewert wird über die "Struktur-Rückgabe" (`sret`) Konvention zurückgegeben, bei der der Aufrufer einen Zeiger auf einen Rückgabespeicher bereitstellt.

Ein Argument oder Rückgabewerte, die ein homogenes Tupel sind, werden manchmal als LLVM-Vektor anstelle eines LLVM-Arrays dargestellt.

## JL Call Convention

Die JL Call-Konvention ist für Built-ins und generische Dispatches. Handgeschriebene Funktionen, die diese Konvention verwenden, werden über das Makro `JL_CALLABLE` deklariert. Die Konvention verwendet genau 3 Parameter:

  * `F`  - Julia-Darstellung der Funktion, die angewendet wird
  * `args` - Zeiger auf ein Array von Zeigern auf Boxen
  * `nargs` - Länge des Arrays

Der Rückgabewert ist ein Zeiger auf eine Box.

## C ABI

C ABI-Wrapper ermöglichen das Aufrufen von Julia aus C. Der Wrapper ruft eine Funktion unter Verwendung der nativen Aufrufkonvention auf.

Tupel werden immer als C-Arrays dargestellt.
