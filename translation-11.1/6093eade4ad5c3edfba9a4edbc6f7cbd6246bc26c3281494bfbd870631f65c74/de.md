```
MIME
```

Ein Typ, der ein standardisiertes Internetdatenformat darstellt. "MIME" steht für "Multipurpose Internet Mail Extensions", da der Standard ursprünglich verwendet wurde, um Multimedia-Anhänge an E-Mail-Nachrichten zu beschreiben.

Ein `MIME`-Objekt kann als zweites Argument an [`show`](@ref) übergeben werden, um die Ausgabe in diesem Format anzufordern.

# Beispiele

```jldoctest
julia> show(stdout, MIME("text/plain"), "hi")
"hi"
```
