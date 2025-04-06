```
LibGit2.git_url(; kwargs...) -> String
```

Créez une chaîne basée sur les composants d'URL fournis. Lorsque le mot-clé `scheme` n'est pas fourni, l'URL produite utilisera la [syntaxe scp-like](https://git-scm.com/docs/git-clone#_git_urls_a_id_urls_a) alternative.

# Mots-clés

  * `scheme::AbstractString=""`: le schéma d'URL qui identifie le protocole à utiliser. Pour HTTP, utilisez "http", pour SSH, utilisez "ssh", etc. Lorsque `scheme` n'est pas fourni, le format de sortie sera "ssh" mais en utilisant la syntaxe scp-like.
  * `username::AbstractString=""`: le nom d'utilisateur à utiliser dans la sortie si fourni.
  * `password::AbstractString=""`: le mot de passe à utiliser dans la sortie si fourni.
  * `host::AbstractString=""`: le nom d'hôte à utiliser dans la sortie. Un nom d'hôte doit être spécifié.
  * `port::Union{AbstractString,Integer}=""`: le numéro de port à utiliser dans la sortie si fourni. Ne peut pas être spécifié lors de l'utilisation de la syntaxe scp-like.
  * `path::AbstractString=""`: le chemin à utiliser dans la sortie si fourni.

!!! avertissement
    Évitez d'utiliser des mots de passe dans les URL. Contrairement aux objets d'identification, Julia n'est pas capable de supprimer ou de détruire de manière sécurisée les données sensibles après utilisation et le mot de passe peut rester en mémoire ; pouvant éventuellement être exposé par une mémoire non initialisée.


# Exemples

```jldoctest
julia> LibGit2.git_url(username="git", host="github.com", path="JuliaLang/julia.git")
"git@github.com:JuliaLang/julia.git"

julia> LibGit2.git_url(scheme="https", host="github.com", path="/JuliaLang/julia.git")
"https://github.com/JuliaLang/julia.git"

julia> LibGit2.git_url(scheme="ssh", username="git", host="github.com", port=2222, path="JuliaLang/julia.git")
"ssh://git@github.com:2222/JuliaLang/julia.git"
```
