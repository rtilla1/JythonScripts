# Use GREL and OpenRefine functions instead (copy into xml2csv documentation later)

## For columns with single name with a role term and code in "[[]]"

1. Split multi-valued cells in column on separator "|"
2. Split cells in column into several columns by separator (two opening square brackets)
3. Split cells in column into several columns by separator "="
3. Remove the column that should now only contain "marcrelator"
3. Text transform cells in column to remove closing square brackets
   > grel:chomp(value, "]]")
4. Split cells in column into several columns by separator "/" into a column for the text and a column for the role
5. Rename your columns. You should now have the "original export name column", a "name string" column, a "role (code)", and a "role (term)" column
6. Run a reconciliation service on your "name string" column, and add a column based on the reconciliation value (conciliator LCNAF recommended)
7. Run a reconciliation service on your "role (code)" and "role (term)" columns and add a column based on these reconciliation values

## For columns with multiple nameParts and roles in [[]]

1. Split multi-valued cells in column on separator "|"
2. Split cells in column into several columns by separator "marcrelator="
3. Text transform cells in column to remove closing square brackets
   > chomp(value, "]]")

Use this in GREL to separate the nameparts from the role terms:
Custom text transform on column name/namePart




leftover Regex or code (may be useful)
> \[{2}(marcrelators\=)([[:alpha:]]{3})(\/(([[:alpha:]]+)([[:blank:]])?([[:alpha:]])*)((]){2}))
> \[{2}(marcrelators\=)([[:alpha:]]{3})
> partition(value,/\[{2}(marcrelators\=)/)
> (^(.)+(, )?(.)+ )\[{2}([[:alpha:]]+\=)([[:alpha:]]+)\/([[:alpha:]]+)\]{2}
