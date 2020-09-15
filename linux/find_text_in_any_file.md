# Find all files containing query text in terminal

To find all the files in a directory containing a specific text (e.g. every file with the function call to `model.predict`), use `grep -rnw '/path/to/somewhere/' -e 'pattern'`

- `-r` or `-R` is recursive,
-`-n` is line number, and
- `-w` stands for match the whole word.
-`-l` (lower-case L) can be added to just give the file name of matching files.

(From https://stackoverflow.com/a/16957078/11956075)
