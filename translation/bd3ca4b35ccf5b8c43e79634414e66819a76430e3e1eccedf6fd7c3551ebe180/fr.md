```
@MIME_str
```

Une macro de commodité pour écrire des types [`MIME`](@ref), généralement utilisée lors de l'ajout de méthodes à [`show`](@ref). Par exemple, la syntaxe `show(io::IO, ::MIME"text/html", x::MyType) = ...` pourrait être utilisée pour définir comment écrire une représentation HTML de `MyType`.
