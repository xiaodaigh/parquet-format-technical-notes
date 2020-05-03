# parquet-format-technical-notes

The first and last 4 bytes of a parquet file are "PAR1".

The 8th-5th last bytes are the metadata size = `meta_len`.

You can read the metadata by seeking to

```
length("PAR1") + data_size
```

where 

```julia
sz = filesize(io)
data_size = (sz - meta_len - 2length("PAR1")-length(size of meta : Int32)) = sz - meta_len - 12
```
