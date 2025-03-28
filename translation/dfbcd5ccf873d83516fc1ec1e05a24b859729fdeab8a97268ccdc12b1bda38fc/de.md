```
arg_readers(arg :: AbstractString, [ type = ArgRead ]) do arg::Function
    ## Vor-Testeinrichtung ##
    @arg_test arg begin
        arg :: ArgRead
        ## Test mit `arg` ##
    end
    ## Nach-Testbereinigung ##
end
```

Die Funktion `arg_readers` nimmt einen Pfad zum Lesen und einen Do-Block mit einem einzelnen Argument, der einmal für jeden Testlesertyp aufgerufen wird, den `arg_read` verarbeiten kann. Wenn das optionale Argument `type` angegeben ist, wird der Do-Block nur für Leser aufgerufen, die Argumente dieses Typs erzeugen.

Das `arg`, das an den Do-Block übergeben wird, ist nicht der Argumentwert selbst, da einige Testargumenttypen für jeden Testfall initialisiert und finalisiert werden müssen. Betrachten Sie ein offenes Dateihandle-Argument: Sobald Sie es für einen Test verwendet haben, können Sie es nicht erneut verwenden; Sie müssen es schließen und die Datei für den nächsten Test erneut öffnen. Diese Funktion `arg` kann in eine `ArgRead`-Instanz umgewandelt werden, indem Sie `@arg_test arg begin ... end` verwenden.
