```
mmap(io::Union{IOStream,AbstractString,Mmap.AnonymousMmap}[, type::Type{Array{T,N}}, dims, offset]; grow::Bool=true, shared::Bool=true)
mmap(type::Type{Array{T,N}}, dims)
```

Erstellen Sie ein `Array`, dessen Werte mit einer Datei verknüpft sind, indem Sie eine Speicherabbildung verwenden. Dies bietet eine bequeme Möglichkeit, mit Daten zu arbeiten, die zu groß sind, um in den Speicher des Computers zu passen.

Der Typ ist ein `Array{T,N}` mit einem Element vom Typ `T` und Dimension `N`, die bestimmt, wie die Bytes des Arrays interpretiert werden. Beachten Sie, dass die Datei im Binärformat gespeichert sein muss und keine Formatkonvertierungen möglich sind (dies ist eine Einschränkung der Betriebssysteme, nicht von Julia).

`dims` ist ein Tupel oder eine einzelne [`Integer`](@ref), die die Größe oder Länge des Arrays angibt.

Die Datei wird über das Stream-Argument übergeben, entweder als geöffnetes [`IOStream`](@ref) oder als Dateinamen-String. Wenn Sie den Stream initialisieren, verwenden Sie `"r"` für ein "schreibgeschütztes" Array und `"w+"`, um ein neues Array zu erstellen, das zum Schreiben von Werten auf die Festplatte verwendet wird.

Wenn kein `type`-Argument angegeben ist, ist der Standard `Vector{UInt8}`.

Optional können Sie einen Offset (in Bytes) angeben, wenn Sie beispielsweise einen Header in der Datei überspringen möchten. Der Standardwert für den Offset ist die aktuelle Stream-Position für ein `IOStream`.

Das Schlüsselwortargument `grow` gibt an, ob die Diskdatei vergrößert werden soll, um die angeforderte Größe des Arrays aufzunehmen (wenn die gesamte Dateigröße < angeforderte Array-Größe ist). Schreibrechte sind erforderlich, um die Datei zu vergrößern.

Das Schlüsselwortargument `shared` gibt an, ob das resultierende `Array` und die daran vorgenommenen Änderungen für andere Prozesse sichtbar sind, die dieselbe Datei abbilden.

Zum Beispiel erstellt der folgende Code

```julia
# Erstellen Sie eine Datei für mmapping
# (Sie könnten alternativ mmap verwenden, um diesen Schritt ebenfalls auszuführen)
using Mmap
A = rand(1:20, 5, 30)
s = open("/tmp/mmap.bin", "w+")
# Wir schreiben die Dimensionen des Arrays als die ersten beiden Ints in die Datei
write(s, size(A,1))
write(s, size(A,2))
# Jetzt die Daten schreiben
write(s, A)
close(s)

# Testen, indem wir es zurücklesen
s = open("/tmp/mmap.bin")   # Standard ist schreibgeschützt
m = read(s, Int)
n = read(s, Int)
A2 = mmap(s, Matrix{Int}, (m,n))
```

ein `m`-by-`n` `Matrix{Int}`, das mit der Datei verknüpft ist, die mit dem Stream `s` verbunden ist.

Eine tragbarere Datei müsste die Wortgröße – 32 Bit oder 64 Bit – und die Endianness-Informationen im Header kodieren. In der Praxis sollten Sie in Betracht ziehen, Binärdaten mit Standardformaten wie HDF5 zu kodieren (das mit Speicherabbildung verwendet werden kann).
