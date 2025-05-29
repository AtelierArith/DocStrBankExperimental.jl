```
sink_prices_to(::Type{OrderedDict},x::OrderedDict{String,Any})
```

Converts an exisitng OrderedDict output from get_prices to an OrderedDict If TimeSeries.jl or TSFrames.jl are loaded this function is extended to allow sinking into these types.
