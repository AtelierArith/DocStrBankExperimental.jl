```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/stdlib/FileWatching/docs/src/index.md"
```

# [File Events](@id lib-filewatching)

```@docs
FileWatching.poll_fd
FileWatching.poll_file
FileWatching.watch_file
FileWatching.watch_folder
FileWatching.unwatch_folder
```

# Pidfile

```@meta
CurrentModule = FileWatching.Pidfile
```

조언 pid 파일(잠금 파일)을 생성하기 위한 간단한 유틸리티 도구입니다.

## Primary Functions

```@docs
mkpidlock
trymkpidlock
close(lock::LockMonitor)
```

## Helper Functions

```@docs
Pidfile.open_exclusive
Pidfile.tryopen_exclusive
Pidfile.write_pidfile
Pidfile.parse_pidfile
Pidfile.stale_pidfile
Pidfile.isvalidpid
Base.touch(::Pidfile.LockMonitor)
```
