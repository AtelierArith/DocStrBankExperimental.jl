```
Pipe()
```

Konstruiere ein nicht initialisiertes Pipe-Objekt, insbesondere für die IO-Kommunikation zwischen mehreren Prozessen.

Das entsprechende Ende der Pipe wird automatisch initialisiert, wenn das Objekt beim Erzeugen von Prozessen verwendet wird. Dies kann nützlich sein, um einfach Referenzen in Prozess-Pipelines zu erhalten, z.B.:

```
julia> err = Pipe()

# Nach diesem `err` wird initialisiert und Sie können `foo`'s
# stderr aus der `err`-Pipe lesen oder `err` an andere Pipelines übergeben.
julia> run(pipeline(pipeline(`foo`, stderr=err), `cat`), wait=false)

# Zerstören Sie jetzt die Schreibhälfte der Pipe, damit die Lesehälfte EOF erhält
julia> closewrite(err)

julia> read(err, String)
"stderr messages"
```

Siehe auch [`Base.link_pipe!`](@ref).
