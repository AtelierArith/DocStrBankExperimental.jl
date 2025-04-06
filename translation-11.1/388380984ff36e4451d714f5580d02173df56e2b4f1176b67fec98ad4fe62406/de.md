```
arg_writers([ type = ArgWrite ]) do path::String, arg::Function
    ## Vor-Testeinrichtung ##
    @arg_test arg begin
        arg :: ArgWrite
        ## Test mit `arg` ##
    end
    ## Nach-Testbereinigung ##
end
```

Die Funktion `arg_writers` nimmt einen do-Block, der einmal für jeden Testschreiber-Typ aufgerufen wird, den `arg_write` verarbeiten kann, mit einem temporären (nicht existierenden) `path` und `arg`, das in verschiedene beschreibbare Argumenttypen umgewandelt werden kann, die in `path` schreiben. Wenn das optionale Argument `type` angegeben ist, wird der do-Block nur für Schreiber aufgerufen, die Argumente dieses Typs erzeugen.

Das `arg`, das an den do-Block übergeben wird, ist nicht der Argumentwert selbst, da einige Testargumenttypen für jeden Testfall initialisiert und finalisiert werden müssen. Betrachten Sie ein offenes Dateihandle-Argument: Sobald Sie es für einen Test verwendet haben, können Sie es nicht erneut verwenden; Sie müssen es schließen und die Datei für den nächsten Test erneut öffnen. Diese Funktion `arg` kann in eine `ArgWrite`-Instanz umgewandelt werden, indem Sie `@arg_test arg begin ... end` verwenden.

Es gibt auch eine `arg_writers`-Methode, die einen Pfadnamen wie `arg_readers` akzeptiert:

```
arg_writers(path::AbstractString, [ type = ArgWrite ]) do arg::Function
    ## Vor-Testeinrichtung ##
    @arg_test arg begin
        # hier `arg :: ArgWrite`
        ## Test mit `arg` ##
    end
    ## Nach-Testbereinigung ##
end
```

Diese Methode ist nützlich, wenn Sie `path` angeben müssen, anstatt den von `tempname()` generierten Pfadnamen zu verwenden. Da `path` von außerhalb von `arg_writers` übergeben wird, ist der Pfad in dieser Form kein Argument für den do-Block.
