# Basic-Bash-Commands
grep 'Branch' infile | awk '{print $3 "\t" $4}'| sed 's/(n=//'| sed 's/(//'|sed 's/)//'| awk  '$2!=""' > outfile
