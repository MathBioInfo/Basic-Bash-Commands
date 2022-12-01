# Basic-Bash-Commands

### `sed`

### `grep`

### `awk`
If we want to print the first column from a file called "inputfile,"  we can use

`awk '{print $1}' inputfile`

`awk '{print $0}' inputfile`

will print everything. which is the same as

`awk '{print}' inputfile`

The following commond

`awk '{print $NF}'`

will print the last columns.

`awk` assumes that 'spaces' are field separators by default, but we can change the field separator to any symbol in `awk`
For example, if we want to use ":" as a field separator, then we use

`awk -F ":" '{print $1}' inputfile`

The following commond will print different columns, separated by ":" and the output must be separated nu Tab "\t"

`awk -F ":" '{print $1"\t"$2"\t"$3}' inputfile`

Columns 1, 2, and 3 in the input file will be separated by ":" in the output file, and out will be separated by "\t."

`awk 'BEGIN{FS=":"; OFE="-"} {print $1, $2, $3}' inputfile`

This is saying to find the ":" treat them as field separators, and as output, print "-" as a field separator. 

`awk -F "/" '/^\// {print $1}'`

treat "/" as a field separator and will search for every line that starts with '/' which is represented by "/," and print the first column of each line. 

`awk 'length($1) > 3' inputfile`

will print column 1 if the there are more than 3 characters. 

### find
The following commond will use `grep` to select all lines starting with word 'Branch' from infile then pipe it and use `awk` to select column 3 and column 4 (separate them by \t) then pipe it (using `sed`) to delete 'n=' pipe it to replace '(' by space or delet it. The output is then piped to delet ')' usind `sed` and finally using `awk` to print column 2. The result willbe stored in 'outfile'

`grep 'Branch' infile | awk '{print $3 "\t" $4}'| sed 's/(n=//'| sed 's/(//'|sed 's/)//'| awk  '$2!=""' > outfile`
