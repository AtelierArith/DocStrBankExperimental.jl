```
countfrom(start=1, step=1)
```

Sonsuz sayan, `start`'ten başlayarak ve `step` kadar artırarak sayan bir yineleyici.

# Örnekler

```jldoctest
julia> for v in Iterators.countfrom(5, 2)
           v > 10 && break
           println(v)
       end
5
7
9
```
