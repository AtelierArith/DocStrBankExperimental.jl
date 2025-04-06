```
LibGit2.ProxyOptions
```

Optionen für die Verbindung über einen Proxy.

Entspricht der [`git_proxy_options`](https://libgit2.org/libgit2/#HEAD/type/git_proxy_options) Struktur.

Die Felder repräsentieren:

  * `version`: Version der verwendeten Struktur, falls sich dies später ändert. Für jetzt immer `1`.
  * `proxytype`: ein `enum` für den Typ des zu verwendenden Proxys. Definiert in [`git_proxy_t`](https://libgit2.org/libgit2/#HEAD/type/git_proxy_t). Das entsprechende Julia-Enum ist `GIT_PROXY` und hat die Werte:

      * `PROXY_NONE`: keine Verbindung über einen Proxy versuchen.
      * `PROXY_AUTO`: versuchen, die Proxy-Konfiguration aus der Git-Konfiguration zu ermitteln.
      * `PROXY_SPECIFIED`: Verbindung unter Verwendung der im `url`-Feld dieser Struktur angegebenen URL herstellen.

    Standardmäßig wird der Proxytyp automatisch erkannt.
  * `url`: die URL des Proxys.
  * `credential_cb`: ein Zeiger auf eine Callback-Funktion, die aufgerufen wird, wenn der Remote-Server eine Authentifizierung zur Verbindung benötigt.
  * `certificate_cb`: ein Zeiger auf eine Callback-Funktion, die aufgerufen wird, wenn die Zertifikatsüberprüfung fehlschlägt. Dies ermöglicht es dem Benutzer zu entscheiden, ob die Verbindung fortgesetzt werden soll oder nicht. Wenn die Funktion `1` zurückgibt, wird die Verbindung erlaubt. Wenn sie `0` zurückgibt, wird die Verbindung nicht erlaubt. Ein negativer Wert kann verwendet werden, um Fehler zurückzugeben.
  * `payload`: die Nutzlast, die den beiden Callback-Funktionen bereitgestellt werden soll.

# Beispiele

```julia-repl
julia> fo = LibGit2.FetchOptions(
           proxy_opts = LibGit2.ProxyOptions(url = Cstring("https://my_proxy_url.com")))

julia> fetch(remote, "master", options=fo)
```
