```
LibGit2.GitStatus(repo::GitRepo; status_opts=StatusOptions())
```

Recopila información sobre el estado de cada archivo en el repositorio git `repo` (por ejemplo, si el archivo está modificado, preparado, etc.). `status_opts` se puede usar para establecer varias opciones, por ejemplo, si se debe o no mirar archivos no rastreados o si se deben incluir submódulos o no. Consulta [`StatusOptions`](@ref) para más información.
