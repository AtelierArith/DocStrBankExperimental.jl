```
LibGit2.CloneOptions
```

Entspricht der [`git_clone_options`](https://libgit2.org/libgit2/#HEAD/type/git_clone_options) Struktur.

Die Felder repräsentieren:

  * `version`: Version der verwendeten Struktur, für den Fall, dass sich dies später ändert. Für jetzt immer `1`.
  * `checkout_opts`: Die Optionen für das Auschecken des Remotes im Rahmen des Klonens.
  * `fetch_opts`: Die Optionen für das Vorab-Abrufen des Remotes im Rahmen des Klonens.
  * `bare`: Wenn `0`, klonen Sie das vollständige Remote-Repository. Wenn ungleich null, führen Sie ein Bare-Klon durch, bei dem es keine lokale Kopie der Quelldateien im Repository gibt und die [`gitdir`](@ref) und [`workdir`](@ref) gleich sind.
  * `localclone`: Flag, ob eine lokale Objekt-Datenbank geklont oder ein Abruf durchgeführt werden soll. Der Standardwert ist, git entscheiden zu lassen. Es wird den git-bewussten Transport für ein lokales Klon nicht verwenden, aber für URLs, die mit `file://` beginnen.
  * `checkout_branch`: Der Name des Branches, der ausgecheckt werden soll. Wenn eine leere Zeichenfolge, wird der Standardbranch des Remotes ausgecheckt.
  * `repository_cb`: Ein optionaler Callback, der verwendet wird, um das *neue* Repository zu erstellen, in das das Klonen erfolgt.
  * `repository_cb_payload`: Die Nutzlast für den Repository-Callback.
  * `remote_cb`: Ein optionaler Callback, der verwendet wird, um das [`GitRemote`](@ref) zu erstellen, bevor das Klonen von ihm erfolgt.
  * `remote_cb_payload`: Die Nutzlast für den Remote-Callback.
