```
countfrom(start=1, step=1)
```

永遠にカウントするイテレータで、`start`から始まり、`step`ずつ増加します。

# 例

```jldoctest
julia> for v in Iterators.countfrom(5, 2)
           v > 10 && break
           println(v)
       end
5
7
9
```
