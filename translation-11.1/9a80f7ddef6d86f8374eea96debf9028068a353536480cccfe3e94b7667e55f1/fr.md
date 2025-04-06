```
@ip_str str -> IPAddr
```

Analyse `str` comme une adresse IP.

# Exemples

```jldoctest
julia> ip"127.0.0.1"
ip"127.0.0.1"

julia> @ip_str "2001:db8:0:0:0:0:2:1"
ip"2001:db8::2:1"
```
