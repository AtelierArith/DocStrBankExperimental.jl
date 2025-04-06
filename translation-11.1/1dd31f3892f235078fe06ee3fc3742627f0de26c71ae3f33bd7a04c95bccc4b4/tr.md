```
worker_id_from_socket(s) -> pid
```

Bir `IO` bağlantısı veya bir `Worker` verildiğinde, bağlı olduğu işçinin `pid`'sini döndüren düşük seviyeli bir API. Bu, bir tür için özel [`serialize`](@ref) yöntemleri yazarken faydalıdır; bu, yazılan verinin alıcı işlem kimliğine bağlı olarak optimize edilmesini sağlar.
