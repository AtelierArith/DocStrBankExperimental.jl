```
trevc!(lado, cuántos, seleccionar, T, VL = similar(T), VR = similar(T))
```

Encuentra el sistema de eigenvalores de una matriz triangular superior `T`. Si `lado = R`, se calculan los eigenvectores derechos. Si `lado = L`, se calculan los eigenvectores izquierdos. Si `lado = B`, se calculan ambos conjuntos. Si `cuántos = A`, se encuentran todos los eigenvectores. Si `cuántos = B`, se encuentran todos los eigenvectores y se transforman de nuevo usando `VL` y `VR`. Si `cuántos = S`, solo se calculan los eigenvectores correspondientes a los valores en `seleccionar`.
