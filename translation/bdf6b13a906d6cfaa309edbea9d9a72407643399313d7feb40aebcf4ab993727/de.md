```
schließlich
```

Führen Sie einen Code aus, wenn ein gegebener Codeblock endet, unabhängig davon, wie er endet. Zum Beispiel, hier ist, wie wir garantieren können, dass eine geöffnete Datei geschlossen wird:

```julia
f = open("file")
try
    operate_on_file(f)
finally
    close(f)
end
```

Wenn die Kontrolle den [`try`](@ref) Block verlässt (zum Beispiel aufgrund eines [`return`](@ref) oder einfach normal endet), wird [`close(f)`](@ref) ausgeführt. Wenn der `try` Block aufgrund einer Ausnahme endet, wird die Ausnahme weiterhin propagiert. Ein `catch` Block kann ebenfalls mit `try` und `finally` kombiniert werden. In diesem Fall wird der `finally` Block ausgeführt, nachdem `catch` den Fehler behandelt hat.
