```
isready(rr::RemoteChannel, args...)
```

Bir [`RemoteChannel`](@ref) içinde bir değer olup olmadığını belirler. Bu işlevin yarış koşullarına neden olabileceğini unutmayın, çünkü sonucu aldığınızda artık doğru olmayabilir. Ancak, yalnızca bir kez atandıkları için [`Future`](@ref) üzerinde güvenle kullanılabilir.
