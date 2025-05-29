```
YAXArray{T,N}
```

An array labelled with named axes that have values associated with them. It can wrap normal arrays or, more typically DiskArrays.

### Fields

  * `axes`: `Tuple` of Dimensions containing the Axes of the Cube
  * `data`: length(axes)-dimensional array which holds the data, this can be a lazy DiskArray
  * `properties`: Metadata properties describing the content of the data
  * `chunks`: Representation of the chunking of the data
  * `cleaner`: Cleaner objects to track which objects to tidy up when the YAXArray goes out of scope
