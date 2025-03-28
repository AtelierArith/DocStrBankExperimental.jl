```
countfrom(start=1, step=1)
```

Un itérateur qui compte indéfiniment, en commençant à `start` et en incrémentant de `step`.

# Exemples

```jldoctest
julia> for v in Iterators.countfrom(5, 2)
           v > 10 && break
           println(v)
       end
5
7
9
```
