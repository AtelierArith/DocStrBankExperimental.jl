```
to_dataset(c;datasetaxis = "Variables", layername = "layer")
```

Convert a Data Cube into a Dataset. It is possible to treat one of the Cube's axes as a `datasetaxis` i.e. the cube will be split into different parts that become variables in the Dataset. If no such axis is specified or found, there will only be a single variable in the dataset with the name `layername`.
