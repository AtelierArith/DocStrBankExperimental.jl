```
fittable(tab,o,fitsym;by=(),weight=nothing)
```

Loops through an iterable table `tab` and thereby fitting an OnlineStat `o` with the values specified through `fitsym`. Optionally one can specify a field (or tuple) to group by. Any groupby specifier can either be a symbol denoting the entry to group by or an anynymous function calculating the group from a table row.

For example the following would caluclate a weighted mean over a cube weighted by grid cell area and grouped by country and month:

```julia
fittable(iter,WeightedMean,:tair,weight=(i->abs(cosd(i.lat))),by=(i->month(i.time),:country))
```
