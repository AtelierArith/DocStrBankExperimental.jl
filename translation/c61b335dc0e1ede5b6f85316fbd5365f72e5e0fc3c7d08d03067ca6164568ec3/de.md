```
stat(file)
```

Gibt eine Struktur zurück, deren Felder Informationen über die Datei enthalten. Die Felder der Struktur sind:

| Name    | Typ                             | Beschreibung                                                                     |
|:------- |:------------------------------- |:-------------------------------------------------------------------------------- |
| desc    | `Union{String, Base.OS_HANDLE}` | Der Pfad oder der OS-Dateideskriptor                                             |
| size    | `Int64`                         | Die Größe (in Bytes) der Datei                                                   |
| device  | `UInt`                          | ID des Geräts, das die Datei enthält                                             |
| inode   | `UInt`                          | Die Inode-Nummer der Datei                                                       |
| mode    | `UInt`                          | Der Schutzmodus der Datei                                                        |
| nlink   | `Int`                           | Die Anzahl der harten Links zur Datei                                            |
| uid     | `UInt`                          | Die Benutzer-ID des Eigentümers der Datei                                        |
| gid     | `UInt`                          | Die Gruppen-ID des Dateieigentümers                                              |
| rdev    | `UInt`                          | Wenn diese Datei auf ein Gerät verweist, die ID des Geräts, auf das sie verweist |
| blksize | `Int64`                         | Die bevorzugte Blockgröße des Dateisystems für die Datei                         |
| blocks  | `Int64`                         | Die Anzahl der zugewiesenen 512-Byte-Blöcke                                      |
| mtime   | `Float64`                       | Unix-Zeitstempel, wann die Datei zuletzt geändert wurde                          |
| ctime   | `Float64`                       | Unix-Zeitstempel, wann die Metadaten der Datei geändert wurden                   |
