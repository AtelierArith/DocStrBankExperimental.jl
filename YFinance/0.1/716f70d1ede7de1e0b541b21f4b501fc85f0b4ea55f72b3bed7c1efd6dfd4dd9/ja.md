```
sink_prices_to(::Type{OrderedDict},x::OrderedDict{String,Any})
```

get_pricesからの既存のOrderedDict出力をOrderedDictに変換します。TimeSeries.jlまたはTSFrames.jlがロードされている場合、この関数はこれらのタイプに沈むことを許可するように拡張されます。
