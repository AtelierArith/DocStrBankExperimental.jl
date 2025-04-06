```
LibGit2.FetchOptions
```

Entspricht der [`git_fetch_options`](https://libgit2.org/libgit2/#HEAD/type/git_fetch_options) Struktur.

Die Felder repräsentieren:

  * `version`: Version der verwendeten Struktur, für den Fall, dass sich dies später ändert. Für jetzt immer `1`.
  * `callbacks`: Remote-Callbacks, die während des Fetch verwendet werden sollen.
  * `prune`: ob nach dem Fetch ein Prune durchgeführt werden soll oder nicht. Der Standard ist, die Einstellung aus der `GitConfig` zu verwenden.
  * `update_fetchhead`: ob das [`FetchHead`](@ref) nach dem Fetch aktualisiert werden soll. Der Standard ist, das Update durchzuführen, was das normale Git-Verhalten ist.
  * `download_tags`: ob Tags, die am Remote vorhanden sind, heruntergeladen werden sollen oder nicht. Der Standard ist, die Tags für Objekte anzufordern, die ohnehin vom Server heruntergeladen werden.
  * `proxy_opts`: Optionen für die Verbindung zum Remote über einen Proxy. Siehe [`ProxyOptions`](@ref). Nur vorhanden in libgit2-Versionen, die neuer oder gleich 0.25.0 sind.
  * `custom_headers`: alle zusätzlichen Header, die für den Fetch benötigt werden. Nur vorhanden in libgit2-Versionen, die neuer oder gleich 0.24.0 sind.
