```
YAML
```

A package to read and write YAML. https://github.com/JuliaData/YAML.jl

Reading:

  * `YAML.load` parses the first YAML document of a YAML file as a Julia object.
  * `YAML.load_all` parses all YAML documents of a YAML file.
  * `YAML.load_file` is the same as `YAML.load` except it reads from a file.
  * `YAML.load_all_file` is the same as `YAML.load_all` except it reads from a file.

Writing:

  * `YAML.write` prints a Julia object as a YAML file.
  * `YAML.write_file` is the same as `YAML.write` except it writes to a file.
  * `YAML.yaml` converts a given Julia object to a YAML-formatted string.
