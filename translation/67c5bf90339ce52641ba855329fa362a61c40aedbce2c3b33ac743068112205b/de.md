```
^(x, y)
```

Exponentiationsoperator.

Wenn `x` und `y` Ganzzahlen sind, kann das Ergebnis überlaufen. Um Zahlen in wissenschaftlicher Notation einzugeben, verwenden Sie [`Float64`](@ref) Literale wie `1.2e3` anstelle von `1.2 * 10^3`.

Wenn `y` ein `Int` Literal ist (z. B. `2` in `x^2` oder `-3` in `x^-3`), wird der Julia-Code `x^y` vom Compiler in `Base.literal_pow(^, x, Val(y))` umgewandelt, um eine Spezialisierung zur Kompilierzeit auf den Wert des Exponenten zu ermöglichen. (Als Standardfallback haben wir `Base.literal_pow(^, x, Val(y)) = ^(x,y)`, wobei normalerweise `^ == Base.^` gilt, es sei denn, `^` wurde im aufrufenden Namensraum definiert.) Wenn `y` ein negatives ganzzahliges Literal ist, transformiert `Base.literal_pow` die Operation standardmäßig in `inv(x)^-y`, wobei `-y` positiv ist.

Siehe auch [`exp2`](@ref), [`<<`](@ref).

# Beispiele

```jldoctest
julia> 3^5
243

julia> 3^-1  # verwendet Base.literal_pow
0.3333333333333333

julia> p = -1;

julia> 3^p
ERROR: DomainError mit -1:
Kann eine Ganzzahl x nicht auf eine negative Potenz -1 heben.
[...]

julia> 3.0^p
0.3333333333333333

julia> 10^19 > 0  # Ganzzahlüberlauf
false

julia> big(10)^19 == 1e19
true
```
