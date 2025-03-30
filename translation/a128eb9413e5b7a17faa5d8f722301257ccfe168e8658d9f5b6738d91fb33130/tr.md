```
add_push!(repo::GitRepo, rmt::GitRemote, push_spec::String)
```

Belirtilen `rmt` için bir *push* refspec ekleyin. Bu refspec, hangi dal(lar)ın itileceği hakkında bilgi içerecektir.

# Örnekler

```julia-repl
julia> LibGit2.add_push!(repo, remote, "refs/heads/master");

julia> remote = LibGit2.get(LibGit2.GitRemote, repo, branch);

julia> LibGit2.push_refspecs(remote)
String["refs/heads/master"]
```

!!! not
    Güncellenen push refspec'leri için değişikliğin etkili olması ve [`push`](@ref) çağrılarının çalışması için ilgili `GitRemote`'u [`close`](@ref) edip yeniden açmanız gerekebilir.

