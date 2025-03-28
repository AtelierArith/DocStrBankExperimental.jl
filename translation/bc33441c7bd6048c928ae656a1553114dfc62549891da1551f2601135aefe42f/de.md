```
homedir() -> String
```

Gibt das Home-Verzeichnis des aktuellen Benutzers zurück.

!!! note
    `homedir` bestimmt das Home-Verzeichnis über `libuv`'s `uv_os_homedir`. Für Details (zum Beispiel, wie man das Home-Verzeichnis über Umgebungsvariablen angibt), siehe die [`uv_os_homedir`-Dokumentation](http://docs.libuv.org/en/v1.x/misc.html#c.uv_os_homedir).


Siehe auch [`Sys.username`](@ref).
