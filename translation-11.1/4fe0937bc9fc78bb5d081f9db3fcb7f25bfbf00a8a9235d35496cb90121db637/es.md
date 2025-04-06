```
commit(repo::GitRepo, msg::AbstractString; kwargs...) -> GitHash
```

Envoltorio alrededor de [`git_commit_create`](https://libgit2.org/libgit2/#HEAD/group/commit/git_commit_create). Crea un commit en el repositorio `repo`. `msg` es el mensaje del commit. Devuelve el OID del nuevo commit.

Los argumentos de palabra clave son:

  * `refname::AbstractString=Consts.HEAD_FILE`: si no es NULL, el nombre de la referencia a actualizar para apuntar al nuevo commit. Por ejemplo, `"HEAD"` actualizará el HEAD de la rama actual. Si la referencia aún no existe, se creará.
  * `author::Signature = Signature(repo)` es una `Signature` que contiene información sobre la persona que creó el commit.
  * `committer::Signature = Signature(repo)` es una `Signature` que contiene información sobre la persona que comprometió el commit en el repositorio. No necesariamente es la misma que `author`, por ejemplo, si `author` envió un parche a `committer` que lo comprometió.
  * `tree_id::GitHash = GitHash()` es un árbol git que se utilizará para crear el commit, mostrando su ascendencia y relación con cualquier otra historia. `tree` debe pertenecer a `repo`.
  * `parent_ids::Vector{GitHash}=GitHash[]` es una lista de commits por [`GitHash`](@ref) que se utilizarán como commits padre para el nuevo, y puede estar vacía. Un commit puede tener múltiples padres si es un commit de fusión, por ejemplo.
