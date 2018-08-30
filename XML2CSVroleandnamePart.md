#Use GREL and OpenRefine functions instead (copy into xml2csv documentation later)

## For columns with multiple nameParts and roles in [[]]
### First, 

### Then,

### Then,

### Use this in GREL to separate the nameparts from the role terms:
Custom text transform on column name/namePart
>partition(value,/\[{2}(marcrelators\=)/)
