```
Parser()
```

Constructeur pour un `Parser` TOML. Notez que dans la plupart des cas, il n'est pas nécessaire de créer explicitement un `Parser`, mais on utilise plutôt directement [`TOML.parsefile`](@ref) ou [`TOML.parse`](@ref). L'utilisation d'un parser explicite réutilisera cependant certaines structures de données internes, ce qui peut être bénéfique pour les performances si un plus grand nombre de petits fichiers sont analysés.
