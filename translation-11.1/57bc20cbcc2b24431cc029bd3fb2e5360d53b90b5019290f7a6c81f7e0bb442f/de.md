```
dlsym_e(handle, sym)
```

Sucht ein Symbol aus einem Shared-Library-Handle und gibt bei einem Lookup-Fehler stillschweigend `C_NULL` zurück. Diese Methode ist jetzt veraltet zugunsten von `dlsym(handle, sym; throw_error=false)`.
