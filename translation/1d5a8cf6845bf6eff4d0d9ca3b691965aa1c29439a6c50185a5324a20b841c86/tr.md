```
islinklocaladdr(addr::IPAddr)
```

Bir IP adresinin bağlantı yerel adresi olup olmadığını test eder. Bağlantı yerel adresleri, ağ segmentlerinin ötesinde benzersiz olma garantisi verilmez, bu nedenle yönlendiriciler bunları iletmez. Bağlantı yerel adresleri `169.254.0.0/16` veya `fe80::/10` adres bloklarından gelir.

# Örnekler

```julia
filter(!islinklocaladdr, getipaddrs())
```
