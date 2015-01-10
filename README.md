# docs-checker

`docs-checker` is a basic utility written in Python 3 for comparing files between two directories, noting those with inconsistencies.



## Documentation

`docs-checker` is run from the command line.  It takes two arguments:

- `--source` which indicates the source directory path, where work is done.

- `--stock` which indicates the staging directory path, which lags behind the source directory.

To run `docs-checker`, use the follow command from the terminal.

```console
$ docs-checker --source /path/to/source/ --stock /path/to/stock
```

The utility generates a list containing all files in the source directory, ignoring Emacs auto-saves, (that is, those files ending in `~` or `#`).  It then generates a listing of the files in the stock directory and compares the two.

Output shows the number of matching files, mismatching files as well as those that are in the source directory, but not stock directory.  It provides a table that gives the filenames for mismatching files with the modification date and time for the source and stock directories, (for instances where the stock file is more up to date).  Lastly it lists the filenames of any instance in the source directory that does not have a match in the stock directory.

```console
$ docs-checker --source ~/Documents/source/ --stock ~/Documents/stock/
[2015-01-10 15:19]
Overview
	Matching Files: 85
	Mismatching Files: 2
	Unmatched Files: 3

Mismatching Files:
+---------------+---------------------+---------------------+
| Filename      | Source              | Stock               |
+---------------+---------------------+---------------------+
| chapter01.rst | 2015-01-10 02:03:15 | 2014-10-03 22:46:31 |
| chapter04.rst | 2014-11-16 23:16:41 | 2014-10-31 06:19:04 |
+---------------+---------------------+---------------------+
Uncopied Files:
chapter33.rst
chapter34.rst
chapter35.rst

```



## Release Notes

### Version 0.1

Initial stable release.