`BroadcastStyle` est un type abstrait et une fonction de trait utilisée pour déterminer le comportement des objets lors de la diffusion. `BroadcastStyle(typeof(x))` renvoie le style associé à `x`. Pour personnaliser le comportement de diffusion d'un type, on peut déclarer un style en définissant une paire type/méthode

```
struct MyContainerStyle <: BroadcastStyle end
Base.BroadcastStyle(::Type{<:MyContainer}) = MyContainerStyle()
```

On écrit ensuite des méthode(s) (au moins [`similar`](@ref)) opérant sur `Broadcasted{MyContainerStyle}`. Il existe également plusieurs sous-types pré-définis de `BroadcastStyle` que vous pouvez exploiter ; consultez le [chapitre Interfaces](@ref man-interfaces-broadcasting) pour plus d'informations.
