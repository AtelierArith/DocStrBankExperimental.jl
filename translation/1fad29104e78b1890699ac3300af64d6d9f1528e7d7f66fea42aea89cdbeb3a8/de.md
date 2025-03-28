```
LibGit2.git_url(; kwargs...) -> String
```

Erstellt eine Zeichenkette basierend auf den bereitgestellten URL-Komponenten. Wenn das Schlüsselwort `scheme` nicht angegeben ist, wird die produzierte URL die alternative [scp-ähnliche Syntax](https://git-scm.com/docs/git-clone#_git_urls_a_id_urls_a) verwenden.

# Schlüsselwörter

  * `scheme::AbstractString=""`: das URL-Schema, das das zu verwendende Protokoll identifiziert. Für HTTP verwenden Sie "http", für SSH "ssh" usw. Wenn `scheme` nicht angegeben ist, wird das Ausgabeformat "ssh" sein, jedoch unter Verwendung der scp-ähnlichen Syntax.
  * `username::AbstractString=""`: der Benutzername, der in der Ausgabe verwendet werden soll, falls angegeben.
  * `password::AbstractString=""`: das Passwort, das in der Ausgabe verwendet werden soll, falls angegeben.
  * `host::AbstractString=""`: der Hostname, der in der Ausgabe verwendet werden soll. Ein Hostname muss angegeben werden.
  * `port::Union{AbstractString,Integer}=""`: die Portnummer, die in der Ausgabe verwendet werden soll, falls angegeben. Kann nicht angegeben werden, wenn die scp-ähnliche Syntax verwendet wird.
  * `path::AbstractString=""`: der Pfad, der in der Ausgabe verwendet werden soll, falls angegeben.

!!! warning
    Vermeiden Sie die Verwendung von Passwörtern in URLs. Im Gegensatz zu den Anmeldeinformationen kann Julia die sensiblen Daten nach der Verwendung nicht sicher nullen oder zerstören, und das Passwort kann im Speicher verbleiben; möglicherweise um von einem nicht initialisierten Speicher exponiert zu werden.


# Beispiele

```jldoctest
julia> LibGit2.git_url(username="git", host="github.com", path="JuliaLang/julia.git")
"git@github.com:JuliaLang/julia.git"

julia> LibGit2.git_url(scheme="https", host="github.com", path="/JuliaLang/julia.git")
"https://github.com/JuliaLang/julia.git"

julia> LibGit2.git_url(scheme="ssh", username="git", host="github.com", port=2222, path="JuliaLang/julia.git")
"ssh://git@github.com:2222/JuliaLang/julia.git"
```
