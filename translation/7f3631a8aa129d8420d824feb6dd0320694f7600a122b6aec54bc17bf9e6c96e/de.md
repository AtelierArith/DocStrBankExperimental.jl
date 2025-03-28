```
open(fd::OS_HANDLE) -> IO
```

Nehmen Sie einen rohen Dateideskriptor, wickeln Sie ihn in einen Julia-bewussten IO-Typ und übernehmen Sie das Eigentum des fd-Handels. Rufen Sie `open(Libc.dup(fd))` auf, um die Eigentumserfassung des ursprünglichen Handgriffs zu vermeiden.

!!! warning
    Rufen Sie dies nicht auf einem Handle auf, das bereits von einem anderen Teil des Systems besessen wird.

