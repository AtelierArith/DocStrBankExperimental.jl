```
muladd(x, y, z)
```

Multiplication-addition combinée : calcule `x*y+z`, mais permet de fusionner l'addition et la multiplication entre elles ou avec des opérations environnantes pour des performances optimales. Par exemple, cela peut être implémenté comme un [`fma`](@ref) si le matériel le prend en charge de manière efficace. Le résultat peut être différent sur différentes machines et peut également varier sur la même machine en raison de la propagation des constantes ou d'autres optimisations. Voir [`fma`](@ref).

# Exemples

```jldoctest
julia> muladd(3, 2, 1)
7

julia> 3 * 2 + 1
7
```
