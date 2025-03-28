```
dlclose(::Nothing)
```

Für das sehr häufige Nutzungsmuster von

```
try
    hdl = dlopen(library_name)
    ... do something
finally
    dlclose(hdl)
end
```

definieren wir eine `dlclose()`-Methode, die einen Parameter vom Typ `Nothing` akzeptiert, damit der Benutzercode sein Verhalten nicht ändern muss, falls `library_name` nicht gefunden wurde.
