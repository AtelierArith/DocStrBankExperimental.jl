# Calling C and Fortran Code

Obwohl der Großteil des Codes in Julia geschrieben werden kann, gibt es viele hochwertige, ausgereifte Bibliotheken für numerische Berechnungen, die bereits in C und Fortran geschrieben wurden. Um die einfache Nutzung dieses bestehenden Codes zu ermöglichen, macht es Julia einfach und effizient, C- und Fortran-Funktionen aufzurufen. Julia verfolgt eine "No Boilerplate"-Philosophie: Funktionen können direkt aus Julia ohne jeglichen "Kleber"-Code, Code-Generierung oder Kompilierung aufgerufen werden – sogar von der interaktiven Eingabeaufforderung. Dies wird erreicht, indem einfach ein entsprechender Aufruf mit dem [`@ccall`](@ref)-Makro (oder der weniger praktischen [`ccall`](@ref)-Syntax, siehe die [`ccall` syntax section](@ref ccall-interface)) gemacht wird.

Der Code, der aufgerufen werden soll, muss als Shared Library verfügbar sein. Die meisten C- und Fortran-Bibliotheken werden bereits als Shared Libraries kompiliert ausgeliefert, aber wenn Sie den Code selbst mit GCC (oder Clang) kompilieren, müssen Sie die Optionen `-shared` und `-fPIC` verwenden. Die von Julias JIT generierten Maschinenanweisungen sind die gleichen wie bei einem nativen C-Aufruf, sodass der resultierende Overhead derselbe ist wie bei einem Aufruf einer Bibliotheksfunktion aus C-Code. [^1]

Standardmäßig ändern Fortran-Compiler [generate mangled names](https://en.wikipedia.org/wiki/Name_mangling#Fortran) (zum Beispiel, indem Funktionsnamen in Klein- oder Großbuchstaben umgewandelt werden, oft mit einem Unterstrich angehängt), und um eine Fortran-Funktion aufzurufen, müssen Sie den mangled Identifier übergeben, der der Regel entspricht, die von Ihrem Fortran-Compiler befolgt wird. Außerdem müssen beim Aufrufen einer Fortran-Funktion alle Eingaben als Zeiger auf zugewiesene Werte im Heap oder Stack übergeben werden. Dies gilt nicht nur für Arrays und andere veränderliche Objekte, die normalerweise im Heap zugewiesen werden, sondern auch für skalare Werte wie Ganzzahlen und Fließkommazahlen, die normalerweise im Stack zugewiesen werden und häufig in Registern übergeben werden, wenn C- oder Julia-Aufrufkonventionen verwendet werden.

Die Syntax für [`@ccall`](@ref), um einen Aufruf der Bibliotheksfunktion zu generieren, ist:

```julia
  @ccall library.function_name(argvalue1::argtype1, ...)::returntype
  @ccall function_name(argvalue1::argtype1, ...)::returntype
  @ccall $function_pointer(argvalue1::argtype1, ...)::returntype
```

wo `library` eine Zeichenkonstante oder ein Literal ist (aber siehe [Non-constant Function Specifications](@ref) unten). Die Bibliothek kann weggelassen werden, in diesem Fall wird der Funktionsname im aktuellen Prozess aufgelöst. Diese Form kann verwendet werden, um C-Bibliotheksfunktionen, Funktionen zur Julia-Laufzeit oder Funktionen in einer mit Julia verlinkten Anwendung aufzurufen. Der vollständige Pfad zur Bibliothek kann ebenfalls angegeben werden. Alternativ kann `@ccall` auch verwendet werden, um einen Funktionszeiger `$function_pointer` aufzurufen, wie er von `Libdl.dlsym` zurückgegeben wird. Die `argtype`s entsprechen der C-Funktionssignatur und die `argvalue`s sind die tatsächlichen Argumentwerte, die an die Funktion übergeben werden sollen.

!!! note
    Siehe unten, wie man [map C types to Julia types](@ref mapping-c-types-to-julia) verwendet.


Als vollständiges, aber einfaches Beispiel ruft der folgende Code die `clock`-Funktion aus der Standard-C-Bibliothek auf den meisten Unix-abgeleiteten Systemen auf:

```julia-repl
julia> t = @ccall clock()::Int32
2292761

julia> typeof(t)
Int32
```

`clock` nimmt keine Argumente und gibt ein `Int32` zurück. Um die Funktion `getenv` aufzurufen, um einen Zeiger auf den Wert einer Umgebungsvariable zu erhalten, tätigt man einen Aufruf wie diesen:

```julia-repl
julia> path = @ccall getenv("SHELL"::Cstring)::Cstring
Cstring(@0x00007fff5fbffc45)

julia> unsafe_string(path)
"/bin/bash"
```

In der Praxis, insbesondere bei der Bereitstellung wiederverwendbarer Funktionalität, wickelt man in der Regel die Verwendung von `@ccall` in Julia-Funktionen ein, die Argumente einrichten und dann auf die Weise auf Fehler überprüfen, die die C- oder Fortran-Funktion angibt. Und wenn ein Fehler auftritt, wird er als normale Julia-Ausnahme ausgelöst. Dies ist besonders wichtig, da C- und Fortran-APIs notorisch inkonsistent darin sind, wie sie Fehlerbedingungen anzeigen. Zum Beispiel wird die C-Bibliotheksfunktion `getenv` in der folgenden Julia-Funktion eingewickelt, die eine vereinfachte Version der tatsächlichen Definition aus [`env.jl`](https://github.com/JuliaLang/julia/blob/master/base/env.jl) ist:

```julia
function getenv(var::AbstractString)
    val = @ccall getenv(var::Cstring)::Cstring
    if val == C_NULL
        error("getenv: undefined variable: ", var)
    end
    return unsafe_string(val)
end
```

Die C-Funktion `getenv` zeigt einen Fehler an, indem sie `C_NULL` zurückgibt, während andere Standard-C-Funktionen Fehler auf unterschiedliche Weise anzeigen, einschließlich durch Rückgabe von -1, 0, 1 und anderen speziellen Werten. Dieser Wrapper wirft eine Ausnahme, die das Problem anzeigt, wenn der Aufrufer versucht, eine nicht vorhandene Umgebungsvariable abzurufen:

```julia-repl
julia> getenv("SHELL")
"/bin/bash"

julia> getenv("FOOBAR")
ERROR: getenv: undefined variable: FOOBAR
```

Hier ist ein etwas komplexeres Beispiel, das den Hostnamen der lokalen Maschine entdeckt.

```julia
function gethostname()
    hostname = Vector{UInt8}(undef, 256) # MAXHOSTNAMELEN
    err = @ccall gethostname(hostname::Ptr{UInt8}, sizeof(hostname)::Csize_t)::Int32
    Base.systemerror("gethostname", err != 0)
    hostname[end] = 0 # ensure null-termination
    return GC.@preserve hostname unsafe_string(pointer(hostname))
end
```

Dieses Beispiel allokiert zunächst ein Array von Bytes. Dann wird die C-Bibliotheksfunktion `gethostname` aufgerufen, um das Array mit dem Hostnamen zu füllen. Schließlich wird ein Zeiger auf den Hostnamen-Puffer genommen und der Zeiger in einen Julia-String umgewandelt, wobei angenommen wird, dass es sich um einen nullterminierten C-String handelt.

Es ist üblich, dass C-Bibliotheken dieses Muster verwenden, bei dem der Aufrufer Speicher zuweisen muss, der an den Aufgerufenen übergeben und befüllt wird. Die Zuweisung von Speicher aus Julia erfolgt in der Regel, indem ein nicht initialisiertes Array erstellt und ein Zeiger auf dessen Daten an die C-Funktion übergeben wird. Aus diesem Grund verwenden wir hier nicht den Typ `Cstring`: Da das Array nicht initialisiert ist, könnte es Null-Bytes enthalten. Die Umwandlung in ein `Cstring` im Rahmen des `@ccall` überprüft auf enthaltene Null-Bytes und könnte daher einen Umwandlungsfehler auslösen.

Das Dereferenzieren von `pointer(hostname)` mit `unsafe_string` ist eine unsichere Operation, da es den Zugriff auf den für `hostname` zugewiesenen Speicher erfordert, der möglicherweise inzwischen garbage collected wurde. Das Makro [`GC.@preserve`](@ref) verhindert dies und somit den Zugriff auf einen ungültigen Speicherort.

Schließlich ist hier ein Beispiel für die Angabe einer Bibliothek über einen Pfad. Wir erstellen eine gemeinsame Bibliothek mit folgendem Inhalt

```c
#include <stdio.h>

void say_y(int y)
{
    printf("Hello from C: got y = %d.\n", y);
}
```

und kompilieren Sie es mit `gcc -fPIC -shared -o mylib.so mylib.c`. Es kann dann aufgerufen werden, indem der (absolute) Pfad als Bibliotheksname angegeben wird:

```julia-repl
julia> @ccall "./mylib.so".say_y(5::Cint)::Cvoid
Hello from C: got y = 5.
```

## Creating C-Compatible Julia Function Pointers

Es ist möglich, Julia-Funktionen an native C-Funktionen zu übergeben, die Funktionszeiger-Argumente akzeptieren. Zum Beispiel, um C-Prototypen der Form zu entsprechen:

```c
typedef returntype (*functiontype)(argumenttype, ...)
```

Die Makro [`@cfunction`](@ref) generiert den C-kompatiblen Funktionszeiger für einen Aufruf einer Julia-Funktion. Die Argumente für `4d61726b646f776e2e436f64652822222c2022406366756e6374696f6e2229_40726566` sind:

1. Eine Julia-Funktion
2. Der Rückgabetyp der Funktion
3. Ein Tupel von Eingabetypen, das der Funktionssignatur entspricht

!!! note
    Wie bei `@ccall` müssen der Rückgabetyp und die Eingabetypen literale Konstanten sein.


!!! note
    Derzeit wird nur die plattformstandardmäßige C-Aufrufkonvention unterstützt. Das bedeutet, dass `@cfunction`-generierte Zeiger nicht in Aufrufen verwendet werden können, bei denen WINAPI eine `stdcall`-Funktion unter 32-Bit-Windows erwartet, aber unter WIN64 verwendet werden können (wo `stdcall` mit der C-Aufrufkonvention vereinheitlicht ist).


!!! note
    Callback-Funktionen, die über `@cfunction` bereitgestellt werden, sollten keine Fehler auslösen, da dies die Kontrolle unerwartet an die Julia-Laufzeit zurückgibt und das Programm möglicherweise in einem undefinierten Zustand hinterlässt.


Ein klassisches Beispiel ist die Standard-C-Bibliotheksfunktion `qsort`, die wie folgt deklariert ist:

```c
void qsort(void *base, size_t nitems, size_t size,
           int (*compare)(const void*, const void*));
```

Das `base`-Argument ist ein Zeiger auf ein Array der Länge `nitems`, mit Elementen von jeweils `size` Bytes. `compare` ist eine Callback-Funktion, die Zeiger auf zwei Elemente `a` und `b` entgegennimmt und eine Ganzzahl kleiner/größer als null zurückgibt, wenn `a` vor/nach `b` erscheinen sollte (oder null, wenn jede Reihenfolge erlaubt ist).

Jetzt nehmen wir an, dass wir ein 1-d Array `A` von Werten in Julia haben, das wir mit der Funktion `qsort` sortieren möchten (anstatt mit Julias eingebauter Funktion `sort`). Bevor wir in Betracht ziehen, `qsort` aufzurufen und Argumente zu übergeben, müssen wir eine Vergleichsfunktion schreiben:

```jldoctest mycompare
julia> function mycompare(a, b)::Cint
           return (a < b) ? -1 : ((a > b) ? +1 : 0)
       end;
```

`qsort` erwartet eine Vergleichsfunktion, die einen C `int` zurückgibt, daher annotieren wir den Rückgabewert als `Cint`.

Um diese Funktion an C zu übergeben, erhalten wir ihre Adresse mit dem Makro `@cfunction`:

```jldoctest mycompare
julia> mycompare_c = @cfunction(mycompare, Cint, (Ref{Cdouble}, Ref{Cdouble}));
```

[`@cfunction`](@ref) benötigt drei Argumente: die Julia-Funktion (`mycompare`), den Rückgabetyp (`Cint`) und ein literales Tupel der Eingabeargumenttypen, in diesem Fall um ein Array von `Cdouble` ([`Float64`](@ref)) Elementen zu sortieren.

Der letzte Aufruf von `qsort` sieht folgendermaßen aus:

```jldoctest mycompare
julia> A = [1.3, -2.7, 4.4, 3.1];

julia> @ccall qsort(A::Ptr{Cdouble}, length(A)::Csize_t, sizeof(eltype(A))::Csize_t, mycompare_c::Ptr{Cvoid})::Cvoid

julia> A
4-element Vector{Float64}:
 -2.7
  1.3
  3.1
  4.4
```

Wie das Beispiel zeigt, wurde das ursprüngliche Julia-Array `A` jetzt sortiert: `[-2.7, 1.3, 3.1, 4.4]`. Beachten Sie, dass Julia [takes care of converting the array to a `Ptr{Cdouble}`](@ref automatic-type-conversion)), die Größe des Elementtyps in Bytes berechnet und so weiter.

Um Spaß zu haben, versuchen Sie, eine `println("mycompare($a, $b)")`-Zeile in `mycompare` einzufügen, die es Ihnen ermöglicht, die Vergleiche zu sehen, die `qsort` durchführt (und zu überprüfen, ob tatsächlich die Julia-Funktion aufgerufen wird, die Sie ihm übergeben haben).

## [Mapping C Types to Julia](@id mapping-c-types-to-julia)

Es ist entscheidend, den deklarierten C-Typ genau mit seiner Deklaration in Julia abzugleichen. Inkonsistenzen können dazu führen, dass Code, der auf einem System korrekt funktioniert, auf einem anderen System fehlschlägt oder unbestimmte Ergebnisse liefert.

Beachten Sie, dass keine C-Header-Dateien im Prozess des Aufrufs von C-Funktionen verwendet werden: Sie sind dafür verantwortlich, dass Ihre Julia-Typen und Funktionssignaturen genau denjenigen in der C-Header-Datei entsprechen.[^2]

### [Automatic Type Conversion](@id automatic-type-conversion)

Julia fügt automatisch Aufrufe der Funktion [`Base.cconvert`](@ref) ein, um jedes Argument in den angegebenen Typ zu konvertieren. Zum Beispiel der folgende Aufruf:

```julia
@ccall "libfoo".foo(x::Int32, y::Float64)::Cvoid
```

wird sich verhalten, als wäre es so geschrieben:

```julia
c_x = Base.cconvert(Int32, x)
c_y = Base.cconvert(Float64, y)
GC.@preserve c_x c_y begin
    @ccall "libfoo".foo(
        Base.unsafe_convert(Int32, c_x)::Int32,
        Base.unsafe_convert(Float64, c_y)::Float64
    )::Cvoid
end
```

[`Base.cconvert`](@ref) ruft normalerweise einfach [`convert`](@ref) auf, kann jedoch so definiert werden, dass es ein beliebiges neues Objekt zurückgibt, das besser geeignet ist, um an C übergeben zu werden. Dies sollte verwendet werden, um alle Speicherzuweisungen durchzuführen, die vom C-Code verwendet werden. Zum Beispiel wird dies verwendet, um ein `Array` von Objekten (z. B. Zeichenfolgen) in ein Array von Zeigern zu konvertieren.

[`Base.unsafe_convert`](@ref) behandelt die Umwandlung in [`Ptr`](@ref) Typen. Es wird als unsicher angesehen, da die Umwandlung eines Objekts in einen nativen Zeiger das Objekt vor dem Garbage Collector verbergen kann, was dazu führt, dass es vorzeitig freigegeben wird.

### Type Correspondences

Zuerst lassen Sie uns einige relevante Julia-Typbegrifflichkeiten überprüfen:

| Syntax / Keyword        | Example                                    | Description                                                                                                                                                                                                                                                       |
|:----------------------- |:------------------------------------------ |:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `mutable struct`        | `BitSet`                                   | "Leaf Type" :: A group of related data that includes a type-tag, is managed by the Julia GC, and is defined by object-identity. The type parameters of a leaf type must be fully defined (no `TypeVars` are allowed) in order for the instance to be constructed. |
| `abstract type`         | `Any`, `AbstractArray{T, N}`, `Complex{T}` | "Super Type" :: A super-type (not a leaf-type) that cannot be instantiated, but can be used to describe a group of types.                                                                                                                                         |
| `T{A}`                  | `Vector{Int}`                              | "Type Parameter" :: A specialization of a type (typically used for dispatch or storage optimization).                                                                                                                                                             |
|                         |                                            | "TypeVar" :: The `T` in the type parameter declaration is referred to as a TypeVar (short for type variable).                                                                                                                                                     |
| `primitive type`        | `Int`, `Float64`                           | "Primitive Type" :: A type with no fields, but a size. It is stored and defined by-value.                                                                                                                                                                         |
| `struct`                | `Pair{Int, Int}`                           | "Struct" :: A type with all fields defined to be constant. It is defined by-value, and may be stored with a type-tag.                                                                                                                                             |
|                         | `ComplexF64` (`isbits`)                    | "Is-Bits"   :: A `primitive type`, or a `struct` type where all fields are other `isbits` types. It is defined by-value, and is stored without a type-tag.                                                                                                        |
| `struct ...; end`       | `nothing`                                  | "Singleton" :: a Leaf Type or Struct with no fields.                                                                                                                                                                                                              |
| `(...)` or `tuple(...)` | `(1, 2, 3)`                                | "Tuple" :: an immutable data-structure similar to an anonymous struct type, or a constant array. Represented as either an array or a struct.                                                                                                                      |

### [Bits Types](@id man-bits-types)

Es gibt mehrere spezielle Typen, die zu beachten sind, da kein anderer Typ definiert werden kann, um sich gleich zu verhalten:

  * `Float32`

    Entspricht genau dem `float`-Typ in C (oder `REAL*4` in Fortran).
  * `Float64`

    Entspricht genau dem `double`-Typ in C (oder `REAL*8` in Fortran).
  * `ComplexF32`

    Entspricht genau dem `complex float` Typ in C (oder `COMPLEX*8` in Fortran).
  * `ComplexF64`

    Entspricht genau dem `complex double` Typ in C (oder `COMPLEX*16` in Fortran).
  * `Unterzeichnet`

    Entspricht genau der `signed` Typannotation in C (oder einem `INTEGER` Typ in Fortran). Jeder Julia-Typ, der kein Subtyp von [`Signed`](@ref) ist, wird als unsigned angenommen.

  * `Ref{T}`

    Verhält sich wie ein `Ptr{T}`, der seinen Speicher über die Julia-GC verwalten kann.

  * `Array{T,N}`

    Wenn ein Array als `Ptr{T}`-Argument an C übergeben wird, wird es nicht uminterpretiert: Julia verlangt, dass der Elementtyp des Arrays mit `T` übereinstimmt, und die Adresse des ersten Elements wird übergeben.

    Daher muss ein `Array`, das Daten im falschen Format enthält, explizit mit einem Aufruf wie `trunc.(Int32, A)` konvertiert werden.

    Um ein Array `A` als Zeiger eines anderen Typs *ohne* vorherige Datenkonvertierung (zum Beispiel, um ein `Float64`-Array an eine Funktion zu übergeben, die mit uninterpretierten Bytes arbeitet), können Sie das Argument als `Ptr{Cvoid}` deklarieren.

    Wenn ein Array vom Typ `Ptr{T}` als Argument vom Typ `Ptr{Ptr{T}}` übergeben wird, wird [`Base.cconvert`](@ref) zunächst versuchen, eine nullterminierte Kopie des Arrays zu erstellen, wobei jedes Element durch seine `4d61726b646f776e2e436f64652822222c2022426173652e63636f6e766572742229_40726566`-Version ersetzt wird. Dies ermöglicht beispielsweise das Übergeben eines `argv`-Zeigerarrays vom Typ `Vector{String}` an ein Argument vom Typ `Ptr{Ptr{Cchar}}`.

Auf allen Systemen, die wir derzeit unterstützen, können grundlegende C/C++-Werttypen wie folgt in Julia-Typen übersetzt werden. Jeder C-Typ hat auch einen entsprechenden Julia-Typ mit demselben Namen, der mit C vorangestellt ist. Dies kann beim Schreiben portabler Codes hilfreich sein (und daran erinnern, dass ein `int` in C nicht dasselbe ist wie ein `Int` in Julia).

**Systemunabhängige Typen**

| C name                                                  | Fortran name             | Standard Julia Alias | Julia Base Type                                                                                             |
|:------------------------------------------------------- |:------------------------ |:-------------------- |:----------------------------------------------------------------------------------------------------------- |
| `unsigned char`                                         | `CHARACTER`              | `Cuchar`             | `UInt8`                                                                                                     |
| `bool` (_Bool in C99+)                                  |                          | `Cuchar`             | `UInt8`                                                                                                     |
| `short`                                                 | `INTEGER*2`, `LOGICAL*2` | `Cshort`             | `Int16`                                                                                                     |
| `unsigned short`                                        |                          | `Cushort`            | `UInt16`                                                                                                    |
| `int`, `BOOL` (C, typical)                              | `INTEGER*4`, `LOGICAL*4` | `Cint`               | `Int32`                                                                                                     |
| `unsigned int`                                          |                          | `Cuint`              | `UInt32`                                                                                                    |
| `long long`                                             | `INTEGER*8`, `LOGICAL*8` | `Clonglong`          | `Int64`                                                                                                     |
| `unsigned long long`                                    |                          | `Culonglong`         | `UInt64`                                                                                                    |
| `intmax_t`                                              |                          | `Cintmax_t`          | `Int64`                                                                                                     |
| `uintmax_t`                                             |                          | `Cuintmax_t`         | `UInt64`                                                                                                    |
| `float`                                                 | `REAL*4i`                | `Cfloat`             | `Float32`                                                                                                   |
| `double`                                                | `REAL*8`                 | `Cdouble`            | `Float64`                                                                                                   |
| `complex float`                                         | `COMPLEX*8`              | `ComplexF32`         | `Complex{Float32}`                                                                                          |
| `complex double`                                        | `COMPLEX*16`             | `ComplexF64`         | `Complex{Float64}`                                                                                          |
| `ptrdiff_t`                                             |                          | `Cptrdiff_t`         | `Int`                                                                                                       |
| `ssize_t`                                               |                          | `Cssize_t`           | `Int`                                                                                                       |
| `size_t`                                                |                          | `Csize_t`            | `UInt`                                                                                                      |
| `void`                                                  |                          |                      | `Cvoid`                                                                                                     |
| `void` and `[[noreturn]]` or `_Noreturn`                |                          |                      | `Union{}`                                                                                                   |
| `void*`                                                 |                          |                      | `Ptr{Cvoid}` (or similarly `Ref{Cvoid}`)                                                                    |
| `T*` (where T represents an appropriately defined type) |                          |                      | `Ref{T}` (T may be safely mutated only if T is an isbits type)                                              |
| `char*` (or `char[]`, e.g. a string)                    | `CHARACTER*N`            |                      | `Cstring` if null-terminated, or `Ptr{UInt8}` if not                                                        |
| `char**` (or `*char[]`)                                 |                          |                      | `Ptr{Ptr{UInt8}}`                                                                                           |
| `jl_value_t*` (any Julia Type)                          |                          |                      | `Any`                                                                                                       |
| `jl_value_t* const*` (a reference to a Julia value)     |                          |                      | `Ref{Any}` (const, since mutation would require a write barrier, which is not possible to insert correctly) |
| `va_arg`                                                |                          |                      | Not supported                                                                                               |
| `...` (variadic function specification)                 |                          |                      | `T...` (where `T` is one of the above types, when using the `ccall` function)                               |
| `...` (variadic function specification)                 |                          |                      | `; va_arg1::T, va_arg2::S, etc.` (only supported with `@ccall` macro)                                       |

Der [`Cstring`](@ref) Typ ist im Wesentlichen ein Synonym für `Ptr{UInt8}`, mit der Ausnahme, dass die Umwandlung in `Cstring` einen Fehler auslöst, wenn der Julia-String eingebettete Nullzeichen enthält (was dazu führen würde, dass der String stillschweigend abgeschnitten wird, wenn die C-Routine Null als Terminator behandelt). Wenn Sie einen `char*` an eine C-Routine übergeben, die keine Nullterminierung annimmt (z. B. weil Sie eine explizite Stringlänge übergeben), oder wenn Sie sich sicher sind, dass Ihr Julia-String keine Null enthält und die Überprüfung überspringen möchten, können Sie `Ptr{UInt8}` als Argumenttyp verwenden. `Cstring` kann auch als Rückgabetyp [`ccall`](@ref) verwendet werden, aber in diesem Fall führt es offensichtlich keine zusätzlichen Überprüfungen ein und soll lediglich die Lesbarkeit des Aufrufs verbessern.

**Systemabhängige Typen**

| C name          | Standard Julia Alias | Julia Base Type                              |
|:--------------- |:-------------------- |:-------------------------------------------- |
| `char`          | `Cchar`              | `Int8` (x86, x86_64), `UInt8` (powerpc, arm) |
| `long`          | `Clong`              | `Int` (UNIX), `Int32` (Windows)              |
| `unsigned long` | `Culong`             | `UInt` (UNIX), `UInt32` (Windows)            |
| `wchar_t`       | `Cwchar_t`           | `Int32` (UNIX), `UInt16` (Windows)           |

!!! note
    Beim Aufruf von Fortran müssen alle Eingaben durch Zeiger auf im Heap oder im Stack zugewiesene Werte übergeben werden, sodass alle oben genannten Typkorrespondenzen einen zusätzlichen `Ptr{..}` oder `Ref{..}` Wrapper um ihre Typspezifikation enthalten sollten.


!!! warning
    Für String-Argumente (`char*`) sollte der Julia-Typ `Cstring` sein (wenn nullterminierte Daten erwartet werden), oder entweder `Ptr{Cchar}` oder `Ptr{UInt8}` andernfalls (diese beiden Zeigertypen haben den gleichen Effekt), wie oben beschrieben, nicht `String`. Ebenso sollte für Array-Argumente (`T[]` oder `T*`) der Julia-Typ wieder `Ptr{T}` sein, nicht `Vector{T}`.


!!! warning
    Julias `Char`-Typ ist 32 Bit, was nicht dasselbe ist wie der Wide-Character-Typ (`wchar_t` oder `wint_t`) auf allen Plattformen.


!!! warning
    Ein Rückgabetyp von `Union{}` bedeutet, dass die Funktion nicht zurückkehrt, d.h. C++11 `[[noreturn]]` oder C11 `_Noreturn` (z.B. `jl_throw` oder `longjmp`). Verwenden Sie dies nicht für Funktionen, die keinen Wert zurückgeben (`void`), aber tatsächlich zurückkehren; für diese verwenden Sie stattdessen `Cvoid`.


!!! note
    Für `wchar_t*`-Argumente sollte der Julia-Typ [`Cwstring`](@ref) sein (wenn die C-Routine einen nullterminierten String erwartet), oder `Ptr{Cwchar_t}` andernfalls. Beachten Sie auch, dass UTF-8-String-Daten in Julia intern nullterminiert sind, sodass sie an C-Funktionen übergeben werden können, die nullterminierte Daten erwarten, ohne eine Kopie zu erstellen (aber die Verwendung des Typs `Cwstring` führt zu einem Fehler, wenn der String selbst Nullzeichen enthält).


!!! note
    C-Funktionen, die ein Argument vom Typ `char**` akzeptieren, können in Julia mit einem `Ptr{Ptr{UInt8}}`-Typ aufgerufen werden. Zum Beispiel C-Funktionen der Form:

    ```c
    int main(int argc, char **argv);
    ```

    kann über den folgenden Julia-Code aufgerufen werden:

    ```julia
    argv = [ "a.out", "arg1", "arg2" ]
    @ccall main(length(argv)::Int32, argv::Ptr{Ptr{UInt8}})::Int32
    ```


!!! note
    Für Fortran-Funktionen, die variabel lange Zeichenfolgen vom Typ `character(len=*)` verwenden, werden die Zeichenfolgenlängen als *versteckte Argumente* bereitgestellt. Typ und Position dieser Argumente in der Liste sind compiler-spezifisch, wobei Compiler-Anbieter normalerweise standardmäßig `Csize_t` als Typ verwenden und die versteckten Argumente am Ende der Argumentliste anhängen. Während dieses Verhalten für einige Compiler (GNU) festgelegt ist, erlauben andere *optional*, die versteckten Argumente direkt nach dem Zeichenfolgenargument zu platzieren (Intel, PGI). Zum Beispiel Fortran-Unterprogramme der Form

    ```fortran
    subroutine test(str1, str2)
    character(len=*) :: str1,str2
    ```

    kann über den folgenden Julia-Code aufgerufen werden, wobei die Längen angehängt werden

    ```julia
    str1 = "foo"
    str2 = "bar"
    ccall(:test, Cvoid, (Ptr{UInt8}, Ptr{UInt8}, Csize_t, Csize_t),
                        str1, str2, sizeof(str1), sizeof(str2))
    ```


!!! warning
    Fortran-Compiler *könnten* auch andere versteckte Argumente für Zeiger, assumed-shape (`:`) und assumed-size (`*`) Arrays hinzufügen. Solches Verhalten kann vermieden werden, indem `ISO_C_BINDING` verwendet und `bind(c)` in der Definition der Unterroutine eingeschlossen wird, was für interoperablen Code dringend empfohlen wird. In diesem Fall wird es keine versteckten Argumente geben, auf Kosten einiger Sprachmerkmale (z. B. wird nur `character(len=1)` erlaubt sein, um Zeichenfolgen zu übergeben).


!!! note
    Eine in C deklarierte Funktion, die `Cvoid` zurückgibt, wird den Wert `nothing` in Julia zurückgeben.


### Struct Type Correspondences

Zusammengesetzte Typen wie `struct` in C oder `TYPE` in Fortran90 (oder `STRUCTURE` / `RECORD` in einigen Varianten von F77) können in Julia gespiegelt werden, indem eine `struct`-Definition mit demselben Feldlayout erstellt wird.

Wenn `isbits`-Typen rekursiv verwendet werden, werden sie inline gespeichert. Alle anderen Typen werden als Zeiger auf die Daten gespeichert. Beim Spiegeln einer Struktur, die by-value innerhalb einer anderen Struktur in C verwendet wird, ist es unerlässlich, dass Sie nicht versuchen, die Felder manuell zu kopieren, da dies die korrekte Feldausrichtung nicht bewahrt. Stattdessen sollten Sie einen `isbits`-Strukturtyp deklarieren und diesen verwenden. Unbenannte Strukturen sind in der Übersetzung nach Julia nicht möglich.

In Julia werden gepackte Strukturen und Union-Deklarationen nicht unterstützt.

Sie können eine Annäherung an ein `union` erhalten, wenn Sie im Voraus wissen, welches Feld die größte Größe haben wird (möglicherweise einschließlich Padding). Wenn Sie Ihre Felder nach Julia übersetzen, deklarieren Sie das Julia-Feld nur als diesen Typ.

Parameterarrays können mit `NTuple` ausgedrückt werden. Zum Beispiel wird die Struktur in C-Notation wie folgt geschrieben:

```c
struct B {
    int A[3];
};

b_a_2 = B.A[2];
```

kann in Julia geschrieben werden als

```julia
struct B
    A::NTuple{3, Cint}
end

b_a_2 = B.A[3]  # note the difference in indexing (1-based in Julia, 0-based in C)
```

Arrays unbekannter Größe (C99-konforme variabel lange Strukturen, die durch `[]` oder `[0]` angegeben sind) werden nicht direkt unterstützt. Oft ist der beste Weg, damit umzugehen, die Byte-Offsets direkt zu behandeln. Wenn beispielsweise eine C-Bibliothek einen ordnungsgemäßen String-Typ deklariert und einen Zeiger darauf zurückgibt:

```c
struct String {
    int strlen;
    char data[];
};
```

In Julia können wir die Teile unabhängig zugreifen, um eine Kopie dieses Strings zu erstellen:

```julia
str = from_c::Ptr{Cvoid}
len = unsafe_load(Ptr{Cint}(str))
unsafe_string(str + Core.sizeof(Cint), len)
```

### Type Parameters

Die Typargumente für `@ccall` und `@cfunction` werden statisch ausgewertet, wenn die Methode, die die Verwendung enthält, definiert wird. Sie müssen daher die Form eines literalen Tupels annehmen, nicht einer Variablen, und dürfen keine lokalen Variablen referenzieren.

Das mag wie eine seltsame Einschränkung erscheinen, aber denken Sie daran, dass C, da es keine dynamische Sprache wie Julia ist, nur Argumenttypen mit einer statisch bekannten, festen Signatur akzeptieren kann.

Allerdings muss das Typlayout statisch bekannt sein, um das beabsichtigte C ABI zu berechnen. Die statischen Parameter der Funktion werden als Teil dieser statischen Umgebung betrachtet. Die statischen Parameter der Funktion können als Typparameter in der Aufrufsignatur verwendet werden, solange sie das Layout des Typs nicht beeinflussen. Zum Beispiel ist `f(x::T) where {T} = @ccall valid(x::Ptr{T})::Ptr{T}` gültig, da `Ptr` immer ein primitiver Typ in Wortgröße ist. Aber `g(x::T) where {T} = @ccall notvalid(x::T)::T` ist nicht gültig, da das Typlayout von `T` nicht statisch bekannt ist.

### SIMD Values

Hinweis: Diese Funktion ist derzeit nur auf 64-Bit-x86- und AArch64-Plattformen implementiert.

Wenn eine C/C++-Routine ein Argument oder einen Rückgabewert hat, der ein natives SIMD-Typ ist, entspricht der entsprechende Julia-Typ einem homogenen Tupel von `VecElement`, das natürlich auf den SIMD-Typ abgebildet wird. Insbesondere:

>   * Das Tupel muss die gleiche Größe wie der SIMD-Typ haben. Zum Beispiel muss ein Tupel, das ein `__m128` auf x86 darstellt, eine Größe von 16 Bytes haben.
>   * Der Elementtyp des Tupels muss eine Instanz von `VecElement{T}` sein, wobei `T` ein primitiver Typ ist, der 1, 2, 4 oder 8 Bytes beträgt.


Zum Beispiel, betrachten Sie diese C-Routine, die AVX-Intrinsics verwendet:

```c
#include <immintrin.h>

__m256 dist( __m256 a, __m256 b ) {
    return _mm256_sqrt_ps(_mm256_add_ps(_mm256_mul_ps(a, a),
                                        _mm256_mul_ps(b, b)));
}
```

Der folgende Julia-Code ruft `dist` mit `ccall` auf:

```julia
const m256 = NTuple{8, VecElement{Float32}}

a = m256(ntuple(i -> VecElement(sin(Float32(i))), 8))
b = m256(ntuple(i -> VecElement(cos(Float32(i))), 8))

function call_dist(a::m256, b::m256)
    @ccall "libdist".dist(a::m256, b::m256)::m256
end

println(call_dist(a,b))
```

Die Host-Maschine muss über die erforderlichen SIMD-Register verfügen. Zum Beispiel wird der obige Code auf Hosts ohne AVX-Unterstützung nicht funktionieren.

### Memory Ownership

**`malloc`/`free`**

Die Speicherzuweisung und -freigabe solcher Objekte muss durch Aufrufe der entsprechenden Bereinigungsroutinen in den verwendeten Bibliotheken erfolgen, genau wie in jedem C-Programm. Versuchen Sie nicht, ein Objekt, das von einer C-Bibliothek mit [`Libc.free`](@ref) in Julia empfangen wurde, freizugeben, da dies dazu führen kann, dass die `free`-Funktion über die falsche Bibliothek aufgerufen wird und der Prozess abbricht. Das Umgekehrte (ein in Julia zugewiesenes Objekt an eine externe Bibliothek zur Freigabe zu übergeben) ist ebenso ungültig.

### When to use `T`, `Ptr{T}` and `Ref{T}`

In Julia-Code, die Aufrufe an externe C-Routinen umschließen, sollten gewöhnliche (nicht-Zeiger) Daten innerhalb des `@ccall` als Typ `T` deklariert werden, da sie durch Wert übergeben werden. Für C-Code, der Zeiger akzeptiert, sollte [`Ref{T}`](@ref) im Allgemeinen für die Typen der Eingabeargumente verwendet werden, was die Verwendung von Zeigern auf von Julia oder C verwalteten Speicher durch den impliziten Aufruf von [`Base.cconvert`](@ref) ermöglicht. Im Gegensatz dazu sollten Zeiger, die von der aufgerufenen C-Funktion zurückgegeben werden, als Ausgabetyp [`Ptr{T}`](@ref) deklariert werden, was widerspiegelt, dass der angezeigte Speicher nur von C verwaltet wird. Zeiger, die in C-Strukturen enthalten sind, sollten als Felder vom Typ `Ptr{T}` innerhalb der entsprechenden Julia-Strukturtypen dargestellt werden, die dazu entworfen sind, die interne Struktur der entsprechenden C-Strukturen nachzuahmen.

In Julia-Code, der Aufrufe an externe Fortran-Routinen umschließt, sollten alle Eingabeargumente als `Ref{T}` deklariert werden, da Fortran alle Variablen durch Zeiger auf Speicherorte übergibt. Der Rückgabetyp sollte entweder `Cvoid` für Fortran-Subroutinen oder ein `T` für Fortran-Funktionen, die den Typ `T` zurückgeben, sein.

## Mapping C Functions to Julia

### `@ccall` / `@cfunction` argument translation guide

Um eine C-Argumentliste in Julia zu übersetzen:

  * `T`, wobei `T` einer der primitiven Typen ist: `char`, `int`, `long`, `short`, `float`, `double`, `complex`, `enum` oder einer ihrer `typedef`-Äquivalente

      * `T`, wobei `T` ein äquivalenter Julia Bits-Typ ist (laut der obigen Tabelle)
      * wenn `T` ein `enum` ist, sollte der Argumenttyp äquivalent zu `Cint` oder `Cuint` sein
      * Argumentwert wird kopiert (per Wert übergeben)
  * `struct T` (einschließlich typedef zu einer Struktur)

      * `T`, wobei `T` ein Julia-Blatttyp ist
      * Argumentwert wird kopiert (per Wert übergeben)
  * `void*`

      * hängt davon ab, wie dieser Parameter verwendet wird, übersetze zuerst in den beabsichtigten Zeigertyp, bestimme dann das entsprechende Julia-Äquivalent unter Verwendung der verbleibenden Regeln in dieser Liste
      * Dieses Argument kann als `Ptr{Cvoid}` deklariert werden, wenn es wirklich nur ein unbekannter Zeiger ist.
  * `jl_value_t*`

      * `Jeder`
      * Das Argument muss ein gültiges Julia-Objekt sein.
  * `jl_value_t* const*`

      * `Ref{Jede}`
      * Die Argumentliste muss ein gültiges Julia-Objekt (oder `C_NULL`) sein.
      * kann nicht für einen Ausgabewert verwendet werden, es sei denn, der Benutzer kann separat dafür sorgen, dass das Objekt GC-erhalten bleibt.
  * `T*`

      * `Ref{T}`, wobei `T` der Julia-Typ ist, der `T` entspricht.
      * Der Argumentwert wird kopiert, wenn es sich um einen `inlinealloc`-Typ handelt (der `isbits` umfasst), andernfalls muss der Wert ein gültiges Julia-Objekt sein.
  * `T (*)(...)` (z. B. ein Zeiger auf eine Funktion)

      * `Ptr{Cvoid}` (Sie müssen möglicherweise [`@cfunction`](@ref) ausdrücklich verwenden, um diesen Zeiger zu erstellen)
  * `...` (z. B. ein Vararg)

      * [für `ccall`]: `T...`, wobei `T` der einzelne Julia-Typ aller verbleibenden Argumente ist
      * [für `@ccall`]: `; va_arg1::T, va_arg2::S, usw.`, wobei `T` und `S` der Julia-Typ sind (d.h. trennen Sie die regulären Argumente von den variadischen Argumenten mit einem `;`)
      * derzeit von `@cfunction` nicht unterstützt
  * `va_arg`

      * nicht unterstützt von `ccall` oder `@cfunction`

### `@ccall` / `@cfunction` return type translation guide

Um einen C-Rückgabetyp in Julia zu übersetzen:

  * `void`

      * `Cvoid` (dies wird die Singleton-Instanz `nothing::Cvoid` zurückgeben)
  * `T`, wobei `T` einer der primitiven Typen ist: `char`, `int`, `long`, `short`, `float`, `double`, `complex`, `enum` oder einer ihrer `typedef`-Äquivalente

      * `T`, wobei `T` ein äquivalenter Julia Bits-Typ ist (laut der obigen Tabelle)
      * wenn `T` ein `enum` ist, sollte der Argumenttyp äquivalent zu `Cint` oder `Cuint` sein
      * Argumentwert wird kopiert (wertbasiert zurückgegeben)
  * `struct T` (einschließlich typedef zu einer Struktur)

      * `T`, wobei `T` ein Julia-Blatttyp ist
      * Argumentwert wird kopiert (wertbasiert zurückgegeben)
  * `void*`

      * hängt davon ab, wie dieser Parameter verwendet wird, übersetze zuerst in den beabsichtigten Zeigertyp, bestimme dann das entsprechende Julia-Äquivalent unter Verwendung der verbleibenden Regeln in dieser Liste
      * Dieses Argument kann als `Ptr{Cvoid}` deklariert werden, wenn es wirklich nur ein unbekannter Zeiger ist.
  * `jl_value_t*`

      * `Jeder`
      * Das Argument muss ein gültiges Julia-Objekt sein.
  * `jl_value_t**`

      * `Ptr{Any}` (`Ref{Any}` ist als Rückgabetyp ungültig)
  * `T*`

      * Wenn der Speicher bereits von Julia besessen wird oder ein `isbits`-Typ ist und als nicht null bekannt ist:

          * `Ref{T}`, wobei `T` der Julia-Typ ist, der `T` entspricht.
          * Ein Rückgabewert vom Typ `Ref{Any}` ist ungültig, er sollte entweder `Any` (entsprechend `jl_value_t*`) oder `Ptr{Any}` (entsprechend `jl_value_t**`) sein.
          * C **DARF NICHT** den Speicher, der über `Ref{T}` zurückgegeben wird, ändern, wenn `T` ein `isbits`-Typ ist.
      * Wenn der Speicher von C besessen wird:

          * `Ptr{T}`, wobei `T` der Julia-Typ ist, der `T` entspricht.
  * `T (*)(...)` (z.B. ein Zeiger auf eine Funktion)

      * `Ptr{Cvoid}` um dies direkt aus Julia aufzurufen, müssen Sie dies als erstes Argument an `@ccall` übergeben. Siehe [Indirect Calls](@ref).

### Passing Pointers for Modifying Inputs

Weil C keine mehrfachen Rückgabewerte unterstützt, nehmen C-Funktionen oft Zeiger auf Daten, die die Funktion ändern wird. Um dies innerhalb eines `@ccall` zu erreichen, müssen Sie zuerst den Wert in einem [`Ref{T}`](@ref) des entsprechenden Typs kapseln. Wenn Sie dieses `Ref`-Objekt als Argument übergeben, wird Julia automatisch einen C-Zeiger auf die gekapselten Daten übergeben:

```julia
width = Ref{Cint}(0)
range = Ref{Cfloat}(0)
@ccall foo(width::Ref{Cint}, range::Ref{Cfloat})::Cvoid
```

Bei der Rückgabe können die Inhalte von `width` und `range` (wenn sie von `foo` geändert wurden) durch `width[]` und `range[]` abgerufen werden; das heißt, sie verhalten sich wie null-dimensionale Arrays.

## C Wrapper Examples

Lass uns mit einem einfachen Beispiel eines C-Wrappers beginnen, der einen `Ptr`-Typ zurückgibt:

```julia
mutable struct gsl_permutation
end

# The corresponding C signature is
#     gsl_permutation * gsl_permutation_alloc (size_t n);
function permutation_alloc(n::Integer)
    output_ptr = @ccall "libgsl".gsl_permutation_alloc(n::Csize_t)::Ptr{gsl_permutation}
    if output_ptr == C_NULL # Could not allocate memory
        throw(OutOfMemoryError())
    end
    return output_ptr
end
```

Der [GNU Scientific Library](https://www.gnu.org/software/gsl/) (hier angenommen, dass er über `:libgsl` zugänglich ist) definiert einen opaken Zeiger, `gsl_permutation *`, als Rückgabetyp der C-Funktion `gsl_permutation_alloc`. Da der Benutzercode niemals in die `gsl_permutation`-Struktur schauen muss, benötigt der entsprechende Julia-Wrapper einfach eine neue Typdeklaration, `gsl_permutation`, die keine internen Felder hat und deren einziger Zweck es ist, im Typparameter eines `Ptr`-Typs platziert zu werden. Der Rückgabetyp von [`ccall`](@ref) wird als `Ptr{gsl_permutation}` deklariert, da der Speicher, der von `output_ptr` zugewiesen und darauf verwiesen wird, von C kontrolliert wird.

Der Eingabewert `n` wird per Wert übergeben, und daher ist die Eingabesignatur der Funktion einfach als `::Csize_t` deklariert, ohne dass `Ref` oder `Ptr` erforderlich sind. (Wenn der Wrapper stattdessen eine Fortran-Funktion aufruft, wäre die entsprechende Eingabesignatur der Funktion stattdessen `::Ref{Csize_t}`, da Fortran-Variablen per Zeiger übergeben werden.) Darüber hinaus kann `n` jeder Typ sein, der in eine `Csize_t`-Ganzzahl umwandelbar ist; der [`ccall`](@ref) ruft implizit [`Base.cconvert(Csize_t, n)`](@ref) auf.

Hier ist ein zweites Beispiel, das den entsprechenden Destruktor umschließt:

```julia
# The corresponding C signature is
#     void gsl_permutation_free (gsl_permutation * p);
function permutation_free(p::Ptr{gsl_permutation})
    @ccall "libgsl".gsl_permutation_free(p::Ptr{gsl_permutation})::Cvoid
end
```

Hier ist ein drittes Beispiel für das Übergeben von Julia-Arrays:

```julia
# The corresponding C signature is
#    int gsl_sf_bessel_Jn_array (int nmin, int nmax, double x,
#                                double result_array[])
function sf_bessel_Jn_array(nmin::Integer, nmax::Integer, x::Real)
    if nmax < nmin
        throw(DomainError())
    end
    result_array = Vector{Cdouble}(undef, nmax - nmin + 1)
    errorcode = @ccall "libgsl".gsl_sf_bessel_Jn_array(
                    nmin::Cint, nmax::Cint, x::Cdouble, result_array::Ref{Cdouble})::Cint
    if errorcode != 0
        error("GSL error code $errorcode")
    end
    return result_array
end
```

Die C-Funktion `wrapped` gibt einen ganzzahligen Fehlercode zurück; die Ergebnisse der tatsächlichen Auswertung der Bessel J-Funktion füllen das Julia-Array `result_array`. Diese Variable wird als `Ref{Cdouble}` deklariert, da ihr Speicher von Julia zugewiesen und verwaltet wird. Der implizite Aufruf von [`Base.cconvert(Ref{Cdouble}, result_array)`](@ref) entpackt den Julia-Zeiger in eine von C verständliche Form für eine Julia-Array-Datenstruktur.

## Fortran Wrapper Example

Das folgende Beispiel verwendet `ccall`, um eine Funktion in einer gemeinsamen Fortran-Bibliothek (libBLAS) aufzurufen, um ein Skalarprodukt zu berechnen. Beachten Sie, dass die Argumentzuordnung hier etwas anders ist als oben, da wir von Julia nach Fortran zuordnen müssen. Bei jedem Argumenttyp geben wir `Ref` oder `Ptr` an. Diese Mangling-Konvention kann spezifisch für Ihren Fortran-Compiler und Ihr Betriebssystem sein und ist wahrscheinlich nicht dokumentiert. Das Einwickeln jedes Arguments in ein `Ref` (oder `Ptr`, wo äquivalent) ist jedoch eine häufige Anforderung von Fortran-Compiler-Implementierungen:

```julia
function compute_dot(DX::Vector{Float64}, DY::Vector{Float64})
    @assert length(DX) == length(DY)
    n = length(DX)
    incx = incy = 1
    product = @ccall "libLAPACK".ddot(
        n::Ref{Int32}, DX::Ptr{Float64}, incx::Ref{Int32}, DY::Ptr{Float64}, incy::Ref{Int32})::Float64
    return product
end
```

## Garbage Collection Safety

Beim Übergeben von Daten an einen `@ccall` ist es am besten, die Funktion [`pointer`](@ref) zu vermeiden. Stattdessen definieren Sie eine Methode [`Base.cconvert`](@ref) und übergeben die Variablen direkt an den `@ccall`. `@ccall` sorgt automatisch dafür, dass alle seine Argumente bis zur Rückkehr des Aufrufs vor der Garbage Collection geschützt sind. Wenn eine C-API eine Referenz auf den von Julia zugewiesenen Speicher speichert, müssen Sie sicherstellen, dass das Objekt für den Garbage Collector sichtbar bleibt, nachdem der `@ccall` zurückgegeben hat. Der empfohlene Weg, dies zu tun, besteht darin, eine globale Variable vom Typ `Array{Ref,1}` zu erstellen, um diese Werte zu halten, bis die C-Bibliothek Ihnen mitteilt, dass sie mit ihnen fertig ist.

Wann immer Sie einen Zeiger auf Julia-Daten erstellt haben, müssen Sie sicherstellen, dass die ursprünglichen Daten existieren, bis Sie den Zeiger nicht mehr verwenden. Viele Methoden in Julia wie [`unsafe_load`](@ref) und [`String`](@ref) erstellen Kopien der Daten, anstatt das Eigentum an dem Puffer zu übernehmen, sodass es sicher ist, die ursprünglichen Daten freizugeben (oder zu ändern), ohne Julia zu beeinträchtigen. Eine bemerkenswerte Ausnahme ist [`unsafe_wrap`](@ref), die aus Leistungsgründen den zugrunde liegenden Puffer teilt (oder gesagt werden kann, dass sie das Eigentum daran übernimmt).

Der Garbage Collector garantiert keine Reihenfolge der Finalisierung. Das heißt, wenn `a` eine Referenz auf `b` enthält und sowohl `a` als auch `b` zur Garbage Collection anstehen, gibt es keine Garantie, dass `b` nach `a` finalisiert wird. Wenn die ordnungsgemäße Finalisierung von `a` davon abhängt, dass `b` gültig ist, muss dies auf andere Weise behandelt werden.

## Non-constant Function Specifications

In einigen Fällen ist der genaue Name oder Pfad der benötigten Bibliothek im Voraus nicht bekannt und muss zur Laufzeit berechnet werden. Um solche Fälle zu behandeln, kann die Spezifikation der Bibliothekskomponente ein Funktionsaufruf sein, z.B. `find_blas().dgemm`. Der Aufrufausdruck wird ausgeführt, wenn der `ccall` selbst ausgeführt wird. Es wird jedoch angenommen, dass sich der Speicherort der Bibliothek nicht ändert, sobald er bestimmt ist, sodass das Ergebnis des Aufrufs zwischengespeichert und wiederverwendet werden kann. Daher ist die Anzahl der Ausführungen des Ausdrucks nicht spezifiziert, und das Zurückgeben unterschiedlicher Werte für mehrere Aufrufe führt zu nicht spezifiziertem Verhalten.

Wenn noch mehr Flexibilität benötigt wird, ist es möglich, berechnete Werte als Funktionsnamen zu verwenden, indem man durch [`eval`](@ref) wie folgt stagniert:

```julia
@eval @ccall "lib".$(string("a", "b"))()::Cint
```

Dieser Ausdruck konstruiert einen Namen mit `string` und setzt diesen Namen dann in einen neuen `@ccall`-Ausdruck ein, der dann ausgewertet wird. Beachten Sie, dass `eval` nur auf der obersten Ebene funktioniert, sodass innerhalb dieses Ausdrucks lokale Variablen nicht verfügbar sind (es sei denn, ihre Werte werden mit `$` ersetzt). Aus diesem Grund wird `eval` typischerweise nur verwendet, um Definitionen auf oberster Ebene zu bilden, zum Beispiel beim Wrapping von Bibliotheken, die viele ähnliche Funktionen enthalten. Ein ähnliches Beispiel kann für [`@cfunction`](@ref) konstruiert werden.

Allerdings wird dies auch sehr langsam sein und Speicherlecks verursachen, daher sollten Sie dies normalerweise vermeiden und stattdessen weiter lesen. Der nächste Abschnitt behandelt, wie man indirekte Aufrufe verwendet, um effizient einen ähnlichen Effekt zu erzielen.

## Indirect Calls

Das erste Argument zu `@ccall` kann auch ein zur Laufzeit ausgewerteter Ausdruck sein. In diesem Fall muss der Ausdruck zu einem `Ptr` ausgewertet werden, der als Adresse der aufzurufenden nativen Funktion verwendet wird. Dieses Verhalten tritt auf, wenn das erste `@ccall`-Argument Verweise auf Nicht-Konstanten enthält, wie lokale Variablen, Funktionsargumente oder nicht-konstante globale Variablen.

Zum Beispiel könnten Sie die Funktion über `dlsym` nachschlagen und sie dann in einem gemeinsamen Verweis für diese Sitzung zwischenspeichern. Zum Beispiel:

```julia
macro dlsym(lib, func)
    z = Ref{Ptr{Cvoid}}(C_NULL)
    quote
        let zlocal = $z[]
            if zlocal == C_NULL
                zlocal = dlsym($(esc(lib))::Ptr{Cvoid}, $(esc(func)))::Ptr{Cvoid}
                $z[] = zlocal
            end
            zlocal
        end
    end
end

mylibvar = Libdl.dlopen("mylib")
@ccall $(@dlsym(mylibvar, "myfunc"))()::Cvoid
```

## Closure cfunctions

Das erste Argument zu [`@cfunction`](@ref) kann mit einem `$` markiert werden, in diesem Fall wird der Rückgabewert stattdessen ein `struct CFunction` sein, das über das Argument schließt. Sie müssen sicherstellen, dass dieses Rückgabeobjekt bis zur vollständigen Nutzung davon lebendig bleibt. Der Inhalt und der Code am cfunction-Zeiger werden über ein [`finalizer`](@ref) gelöscht, wenn diese Referenz fallen gelassen wird und atexit. Dies ist normalerweise nicht erforderlich, da diese Funktionalität in C nicht vorhanden ist, kann jedoch nützlich sein, um mit schlecht gestalteten APIs umzugehen, die keinen separaten Parameter für die Closure-Umgebung bereitstellen.

```julia
function qsort(a::Vector{T}, cmp) where T
    isbits(T) || throw(ArgumentError("this method can only qsort isbits arrays"))
    callback = @cfunction $cmp Cint (Ref{T}, Ref{T})
    # Here, `callback` isa Base.CFunction, which will be converted to Ptr{Cvoid}
    # (and protected against finalization) by the ccall
    @ccall qsort(a::Ptr{T}, length(a)::Csize_t, Base.elsize(a)::Csize_t, callback::Ptr{Cvoid})
    # We could instead use:
    #    GC.@preserve callback begin
    #        use(Base.unsafe_convert(Ptr{Cvoid}, callback))
    #    end
    # if we needed to use it outside of a `ccall`
    return a
end
```

!!! note
    Die Closure [`@cfunction`](@ref) ist auf LLVM-Trampolinen angewiesen, die nicht auf allen Plattformen verfügbar sind (zum Beispiel ARM und PowerPC).


## Closing a Library

Es ist manchmal nützlich, eine Bibliothek zu schließen (zu entladen), damit sie neu geladen werden kann. Zum Beispiel, wenn man C-Code für die Verwendung mit Julia entwickelt, muss man möglicherweise den C-Code kompilieren, den C-Code aus Julia aufrufen, dann die Bibliothek schließen, eine Bearbeitung vornehmen, neu kompilieren und die neuen Änderungen laden. Man kann entweder Julia neu starten oder die `Libdl`-Funktionen verwenden, um die Bibliothek explizit zu verwalten, wie zum Beispiel:

```julia
lib = Libdl.dlopen("./my_lib.so") # Open the library explicitly.
sym = Libdl.dlsym(lib, :my_fcn)   # Get a symbol for the function to call.
@ccall $sym(...) # Use the pointer `sym` instead of the library.symbol tuple.
Libdl.dlclose(lib) # Close the library explicitly.
```

Beachten Sie, dass beim Verwenden von `@ccall` mit dem Eingabewert (z. B. `@ccall "./my_lib.so".my_fcn(...)::Cvoid`) die Bibliothek implizit geöffnet wird und möglicherweise nicht explizit geschlossen wird.

## Variadic function calls

Um variadische C-Funktionen aufzurufen, kann ein `Semikolon` in der Argumentliste verwendet werden, um erforderliche Argumente von variadischen Argumenten zu trennen. Ein Beispiel mit der `printf`-Funktion ist unten angegeben:

```julia-repl
julia> @ccall printf("%s = %d\n"::Cstring ; "foo"::Cstring, foo::Cint)::Cint
foo = 3
8
```

## [`ccall` interface](@id ccall-interface)

Es gibt eine weitere alternative Schnittstelle zu `@ccall`. Diese Schnittstelle ist etwas weniger bequem, ermöglicht es jedoch, eine [calling convention](@ref calling-convention) anzugeben.

Die Argumente zu [`ccall`](@ref) sind:

1. Ein `(:function, "library")` Paar (am häufigsten),

    ODER

    ein `:function` Namenssymbol oder ein `"function"` Namensstring (für Symbole im aktuellen Prozess oder libc),

    ODER

    ein Funktionszeiger (zum Beispiel von `dlsym`).
2. Der Rückgabetyp der Funktion
3. Ein Tupel von Eingabetypen, das der Funktionssignatur entspricht. Ein häufiger Fehler ist zu vergessen, dass ein 1-Tupel von Argumenttypen mit einem nachgestellten Komma geschrieben werden muss.
4. Die tatsächlichen Argumentwerte, die an die Funktion übergeben werden sollen, falls vorhanden; jedes ist ein separates Parameter.

!!! note
    Das `(:function, "library")` Paar, der Rückgabetyp und die Eingabetypen müssen literale Konstanten sein (d.h. sie können keine Variablen sein, aber siehe [Non-constant Function Specifications](@ref)).

    Die verbleibenden Parameter werden zur Compile-Zeit ausgewertet, wenn die enthaltene Methode definiert wird.


Eine Tabelle mit Übersetzungen zwischen der Makro- und der Funktionsschnittstelle ist unten angegeben.

|                                                                     `@ccall` |                                                                     `ccall` |
| ----------------------------------------------------------------------------:| ---------------------------------------------------------------------------:|
|                                                      `@ccall clock()::Int32` |                                                  `ccall(:clock, Int32, ())` |
|                                                    `@ccall f(a::Cint)::Cint` |                                               `ccall(:a, Cint, (Cint,), a)` |
|                               `@ccall "mylib".f(a::Cint, b::Cdouble)::Cvoid` |                      `ccall((:f, "mylib"), Cvoid, (Cint, Cdouble), (a, b))` |
|                                                    `@ccall $fptr.f()::Cvoid` |                                                 `ccall(fptr, f, Cvoid, ())` |
|      `@ccall printf("%s = %d\n"::Cstring ; "foo"::Cstring, foo::Cint)::Cint` |                                                             `<unavailable>` |
| `@ccall printf("%s = %s\n"::Cstring ; "2 + 2"::Cstring, "5"::Cstring)::Cint` |    `ccall(:printf, Cint, (Cstring, Cstring...), "%s = %s\n", "2 + 2", "5")` |
|                                                              `<unavailable>` | `ccall(:gethostname, stdcall, Int32, (Ptr{UInt8}, UInt32), hn, length(hn))` |

## [Calling Convention](@id calling-convention)

Das zweite Argument zu `ccall` (unmittelbar vor dem Rückgabetyp) kann optional ein Spezifizierer für die Aufrufkonvention sein (das `@ccall`-Makro unterstützt derzeit nicht die Angabe einer Aufrufkonvention). Ohne einen Spezifizierer wird die plattformstandardmäßige C-Aufrufkonvention verwendet. Andere unterstützte Konventionen sind: `stdcall`, `cdecl`, `fastcall` und `thiscall` (kein Effekt auf 64-Bit Windows). Zum Beispiel (aus `base/libc.jl`) sehen wir dasselbe `gethostname``ccall` wie oben, aber mit der korrekten Signatur für Windows:

```julia
hn = Vector{UInt8}(undef, 256)
err = ccall(:gethostname, stdcall, Int32, (Ptr{UInt8}, UInt32), hn, length(hn))
```

Für weitere Informationen siehe [LLVM Language Reference](https://llvm.org/docs/LangRef.html#calling-conventions).

Es gibt eine zusätzliche spezielle Aufrufkonvention [`llvmcall`](@ref Base.llvmcall), die das Einfügen von Aufrufen zu LLVM-Intrinsics direkt ermöglicht. Dies kann besonders nützlich sein, wenn man auf ungewöhnliche Plattformen wie GPGPUs abzielt. Zum Beispiel müssen wir für [CUDA](https://llvm.org/docs/NVPTXUsage.html) in der Lage sein, den Thread-Index zu lesen:

```julia
ccall("llvm.nvvm.read.ptx.sreg.tid.x", llvmcall, Int32, ())
```

Wie bei jedem `ccall` ist es wichtig, die Argumentsignatur genau richtig zu bekommen. Beachten Sie auch, dass es keine Kompatibilitätsschicht gibt, die sicherstellt, dass das Intrinsic sinnvoll ist und auf dem aktuellen Ziel funktioniert, im Gegensatz zu den entsprechenden Julia-Funktionen, die von `Core.Intrinsics` bereitgestellt werden.

## Accessing Global Variables

Globale Variablen, die von nativen Bibliotheken exportiert werden, können über den Namen mit der Funktion [`cglobal`](@ref) zugegriffen werden. Die Argumente für `4d61726b646f776e2e436f64652822222c202263676c6f62616c2229_40726566` sind eine Symbolbeschreibung, die identisch ist mit der, die von [`ccall`](@ref) verwendet wird, und einem Typ, der den in der Variablen gespeicherten Wert beschreibt:

```julia-repl
julia> cglobal((:errno, :libc), Int32)
Ptr{Int32} @0x00007f418d0816b8
```

Das Ergebnis ist ein Zeiger, der die Adresse des Wertes angibt. Der Wert kann über diesen Zeiger mit [`unsafe_load`](@ref) und [`unsafe_store!`](@ref) manipuliert werden.

!!! note
    Dieses `errno`-Symbol ist möglicherweise nicht in einer Bibliothek namens "libc" zu finden, da dies ein Implementierungsdetail Ihres Systemcompilers ist. Typischerweise sollten Symbole der Standardbibliothek nur nach Namen aufgerufen werden, sodass der Compiler das richtige einfügen kann. Das `errno`-Symbol, das in diesem Beispiel gezeigt wird, ist jedoch in den meisten Compilern besonders, und der hier angezeigte Wert entspricht wahrscheinlich nicht dem, was Sie erwarten oder wollen. Das Kompilieren des entsprechenden Codes in C auf einem beliebigen system mit Multi-Threading-Fähigkeit würde typischerweise tatsächlich eine andere Funktion aufrufen (über Makro-Preprozessor-Überladung) und könnte ein anderes Ergebnis liefern als der hier ausgegebene Legacy-Wert.


## Accessing Data through a Pointer

Die folgenden Methoden werden als "unsicher" beschrieben, da ein fehlerhafter Zeiger oder eine falsche Typdeklaration dazu führen kann, dass Julia abrupt beendet wird.

Gegeben einem `Ptr{T}` können die Inhalte des Typs `T` im Allgemeinen aus dem referenzierten Speicher in ein Julia-Objekt mit `unsafe_load(ptr, [index])` kopiert werden. Das Index-Argument ist optional (Standard ist 1) und folgt der Julia-Konvention der 1-basierten Indizierung. Diese Funktion ist absichtlich ähnlich im Verhalten zu [`getindex`](@ref) und [`setindex!`](@ref) (z. B. `[]` Zugriffs-Syntax).

Der Rückgabewert ist ein neues Objekt, das so initialisiert wird, dass es eine Kopie des Inhalts des referenzierten Speichers enthält. Der referenzierte Speicher kann sicher freigegeben oder freigesetzt werden.

Wenn `T` `Any` ist, wird angenommen, dass der Speicher einen Verweis auf ein Julia-Objekt (ein `jl_value_t*`) enthält, das Ergebnis wird ein Verweis auf dieses Objekt sein, und das Objekt wird nicht kopiert. Sie müssen in diesem Fall darauf achten, dass das Objekt immer für den Garbage Collector sichtbar ist (Zeiger zählen nicht, aber der neue Verweis tut es), um sicherzustellen, dass der Speicher nicht vorzeitig freigegeben wird. Beachten Sie, dass, wenn das Objekt ursprünglich nicht von Julia zugewiesen wurde, das neue Objekt niemals von Julias Garbage Collector finalisiert wird. Wenn der `Ptr` tatsächlich ein `jl_value_t*` ist, kann er mit [`unsafe_pointer_to_objref(ptr)`](@ref) wieder in einen Verweis auf ein Julia-Objekt umgewandelt werden. (Julia-Werte `v` können in `jl_value_t*`-Zeiger, als `Ptr{Cvoid}`, umgewandelt werden, indem [`pointer_from_objref(v)`](@ref) aufgerufen wird.)

Die Umkehroperation (Schreiben von Daten in ein `Ptr{T}`) kann unter Verwendung von [`unsafe_store!(ptr, value, [index])`](@ref) durchgeführt werden. Derzeit wird dies nur für primitive Typen oder andere zeigerfreie (`isbits`) unveränderliche Strukturtypen unterstützt.

Jede Operation, die einen Fehler auslöst, ist wahrscheinlich derzeit nicht implementiert und sollte als Fehler gemeldet werden, damit sie behoben werden kann.

Wenn der interessierende Zeiger ein einfaches Datenarray (primitive Typen oder unveränderliche Strukturen) ist, könnte die Funktion [`unsafe_wrap(Array, ptr,dims, own = false)`](@ref) nützlicher sein. Der letzte Parameter sollte wahr sein, wenn Julia "das Eigentum" des zugrunde liegenden Puffers übernehmen und `free(ptr)` aufrufen soll, wenn das zurückgegebene `Array`-Objekt finalisiert wird. Wenn der `own`-Parameter weggelassen oder falsch ist, muss der Aufrufer sicherstellen, dass der Puffer bis zum Abschluss aller Zugriffe vorhanden bleibt.

Arithmetik mit dem `Ptr`-Typ in Julia (z. B. mit `+`) verhält sich nicht wie die Zeigerarithmetik in C. Das Hinzufügen einer Ganzzahl zu einem `Ptr` in Julia verschiebt den Zeiger immer um eine bestimmte Anzahl von *Bytes*, nicht von Elementen. Auf diese Weise hängen die durch die Zeigerarithmetik erhaltenen Adresswerte nicht von den Elementtypen der Zeiger ab.

## Thread-safety

Einige C-Bibliotheken führen ihre Rückrufe aus einem anderen Thread aus, und da Julia nicht threadsicher ist, müssen Sie einige zusätzliche Vorsichtsmaßnahmen treffen. Insbesondere müssen Sie ein zweischichtiges System einrichten: Der C-Rückruf sollte nur die Ausführung Ihres "echten" Rückrufs *planen* (über die Ereignisschleife von Julia). Um dies zu tun, erstellen Sie ein [`AsyncCondition`](@ref Base.AsyncCondition)-Objekt und [`wait`](@ref) darauf:

```julia
cond = Base.AsyncCondition()
wait(cond)
```

Der Callback, den Sie an C übergeben, sollte nur einen [`ccall`](@ref) an `:uv_async_send` ausführen, wobei `cond.handle` als Argument übergeben wird, und darauf geachtet werden sollte, dass keine Allokationen oder andere Interaktionen mit der Julia-Laufzeit stattfinden.

Beachten Sie, dass Ereignisse zusammengefasst werden können, sodass mehrere Aufrufe von `uv_async_send` zu einer einzigen Weckbenachrichtigung an die Bedingung führen können.

## More About Callbacks

Für weitere Details, wie man Callbacks an C-Bibliotheken übergibt, siehe dies [blog post](https://julialang.org/blog/2013/05/callback).

## C++

Für Werkzeuge zur Erstellung von C++-Bindings siehe das [CxxWrap](https://github.com/JuliaInterop/CxxWrap.jl)-Paket.

[^1]: Non-library function calls in both C and Julia can be inlined and thus may have even less overhead than calls to shared library functions. The point above is that the cost of actually doing foreign function call is about the same as doing a call in either native language.

[^2]: The [Clang package](https://github.com/ihnorton/Clang.jl) can be used to auto-generate Julia code from a C header file.
