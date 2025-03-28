```
Downloader(; [ grace::Real = 30 ])
```

Los objetos `Downloader` se utilizan para realizar operaciones de `download` individuales. Las conexiones, las búsquedas de nombres y otros recursos se comparten dentro de un `Downloader`. Estas conexiones y recursos se limpian después de un período de gracia configurable (por defecto: 30 segundos) desde que se descargó algo con él, o cuando se recolecta como basura, lo que ocurra primero. Si el período de gracia se establece en cero, todos los recursos se limpiarán inmediatamente tan pronto como no haya más descargas en curso. Si el período de gracia se establece en `Inf`, entonces los recursos no se limpiarán hasta que el `Downloader` sea recolectado como basura.
