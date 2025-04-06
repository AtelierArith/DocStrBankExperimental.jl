```
write(io::IO, x)
```

Schreiben Sie die kanonische binäre Darstellung eines Wertes in den angegebenen I/O-Stream oder die Datei. Gibt die Anzahl der in den Stream geschriebenen Bytes zurück. Siehe auch [`print`](@ref), um eine Textdarstellung zu schreiben (mit einer Kodierung, die von `io` abhängen kann).

Die Endianness des geschriebenen Wertes hängt von der Endianness des Host-Systems ab. Konvertieren Sie zu/von einer festen Endianness beim Schreiben/Lesen (z. B. unter Verwendung von [`htol`](@ref) und [`ltoh`](@ref)), um Ergebnisse zu erhalten, die plattformübergreifend konsistent sind.

Sie können mehrere Werte mit demselben `write`-Aufruf schreiben. d.h. die folgenden sind äquivalent:

```
write(io, x, y...)
write(io, x) + write(io, y...)
```

# Beispiele

Konsistente Serialisierung:

```jldoctest
julia> fname = tempname(); # zufälliger temporärer Dateiname

julia> open(fname,"w") do f
           # Stellen Sie sicher, dass wir 64-Bit-Ganzzahlen in kleiner Endian-Byte-Reihenfolge schreiben
           write(f,htol(Int64(42)))
       end
8

julia> open(fname,"r") do f
           # Konvertieren Sie zurück in die Host-Byte-Reihenfolge und den Host-Ganzzahltyp
           Int(ltoh(read(f,Int64)))
       end
42
```

Zusammenführen von Schreibaufrufen:

```jldoctest
julia> io = IOBuffer();

julia> write(io, "JuliaLang ist eine GitHub-Organisation.", " Es hat viele Mitglieder.")
56

julia> String(take!(io))
"JuliaLang ist eine GitHub-Organisation. Es hat viele Mitglieder."

julia> write(io, "Manchmal schreiben diese Mitglieder") + write(io, " Dokumentation.")
44

julia> String(take!(io))
"Manchmal schreiben diese Mitglieder Dokumentation."
```

Benutzerdefinierte einfache Datentypen ohne `write`-Methoden können geschrieben werden, wenn sie in einem `Ref` verpackt sind:

```jldoctest
julia> struct MyStruct; x::Float64; end

julia> io = IOBuffer()
IOBuffer(data=UInt8[...], readable=true, writable=true, seekable=true, append=false, size=0, maxsize=Inf, ptr=1, mark=-1)

julia> write(io, Ref(MyStruct(42.0)))
8

julia> seekstart(io); read!(io, Ref(MyStruct(NaN)))
Base.RefValue{MyStruct}(MyStruct(42.0))
```
