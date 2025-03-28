```
LibGit2.PushOptions
```

Entspricht der [`git_push_options`](https://libgit2.org/libgit2/#HEAD/type/git_push_options) Struktur.

Die Felder repräsentieren:

  * `version`: Version der verwendeten Struktur, für den Fall, dass sich dies später ändert. Für jetzt immer `1`.
  * `parallelism`: Wenn eine Packdatei erstellt werden muss, legt diese Variable die Anzahl der Arbeits-Threads fest, die vom Packbuilder gestartet werden. Wenn `0`, wird der Packbuilder die Anzahl der zu verwendenden Threads automatisch festlegen. Der Standardwert ist `1`.
  * `callbacks`: die Rückruffunktionen (z. B. für die Authentifizierung mit dem Remote), die für den Push verwendet werden sollen.
  * `proxy_opts`: nur relevant, wenn die LibGit2-Version größer oder gleich `0.25.0` ist. Legt Optionen für die Verwendung eines Proxys zur Kommunikation mit einem Remote fest. Siehe [`ProxyOptions`](@ref) für weitere Informationen.
  * `custom_headers`: nur relevant, wenn die LibGit2-Version größer oder gleich `0.24.0` ist. Zusätzliche Header, die für den Push-Vorgang benötigt werden.
