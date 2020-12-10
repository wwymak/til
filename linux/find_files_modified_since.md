# Finding files you have modified since a date

For example, you are running a script to update all the files in a directory, and you want to find out how far you have gone.

`find . -maxdepth 1 -newermt "2020-12-10" | wc -l` will spit out how many files have been modified since midnight 2020-12-10.
