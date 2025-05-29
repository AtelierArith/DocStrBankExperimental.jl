```
create_proxy_settings(p::AbstractString,user=nothing,password=nothing)
```

Sets the global proxy variable `_PROXY_SETTINGS::NamedTuple`. This `NamedTuple` contains a `proxy` and a `auth` field. These fields default to `nothing` and and empty `Dict` respectively.

## Arguments

  * p`::String` (Required) of the form: "http://proxy.xyz.com:8080"
  * user`::String` Username (optional) only required if proxy requires authentication. Defaults to `nothing` (no authentication needed)
  * password`::String` The password corresponding to the Username. Defaults to `nothing` (no authentication needed)
