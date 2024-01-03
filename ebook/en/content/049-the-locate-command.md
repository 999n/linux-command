# The `locate` command

The `locate` command searches the file system for files and directories whose name matches a given pattern through a database file that is generated by the `updatedb` command.

### Examples:

1. Running the `locate` command to search for a file named `.bashrc`.

```
locate .bashrc
```
*Output*
```
/etc/bash.bashrc
/etc/skel/.bashrc
/home/linuxize/.bashrc
/usr/share/base-files/dot.bashrc
/usr/share/doc/adduser/examples/adduser.local.conf.examples/bash.bashrc
/usr/share/doc/adduser/examples/adduser.local.conf.examples/skel/dot.bashrc
```
The `/root/.bashrc` file will not be shown because we ran the command as a normal user that doesn’t have access permissions to the `/root` directory.

If the result list is long, for better readability, you can pipe the output to the  [`less`](https://linuxize.com/post/less-command-in-linux/)  command:

```
locate .bashrc | less
```

2. To search for all `.md` files on the system
```
locate *.md
```
3. To search all `.py` files and display only 10 results
```
locate -n 10 *.py
```
4. To performs case-insensitive search.
```
locate -i readme.md
```
*Output*
```
/home/linuxize/p1/readme.md
/home/linuxize/p2/README.md
/home/linuxize/p3/ReadMe.md
```
5. To return the number of all files containing `.bashrc` in their name.
```
locate -c .bashrc
```
*Output*
```
6
```
6. The following would return only the existing `.json` files on the file system.
```
locate -e *.json
```
7. To run a more complex search the `-r` (`--regexp`) option is used. 
To search for all `.mp4` and `.avi` files on your system and ignore case.
```
locate --regex -i "(\.mp4|\.avi)"
```

### Syntax:

```
1.  locate [OPTION]... PATTERN...
```


### Additional Flags and their Functionalities:

|**Short Flag**   |**Long Flag**   |**Description**   |
|:---|:---|:---|
|`-A`|`--all`|It is used to display only entries that match all PATTERNs instead of requiring only one of them to match.|
|`-b`|`--basename`|It is used to match only the base name against the specified patterns.|
|`-c`|`--count`|It is used for writing the number matching entries instead of writing file names on standard output.|
|`-d`|`--database DBPATH`|It is used to replace the default database with DBPATH.|
|`-e`|`--existing`|It is used to display only entries that refer to existing files during the command is executed.|
|`-L`|`--follow`|If the `--existing` option is specified, It is used for checking whether files exist and follow trailing symbolic links. It will omit the broken symbolic links to the output. This is the default behavior. The opposite behavior can be specified using the `--nofollow` option.|
|`-h`|`--help`|It is used to display the help documentation that contains a summary of the available options.|
|`-i`|`--ignore-case`|It is used to ignore case sensitivity of the specified patterns.|
|`-p`|`--ignore-spaces`|It is used to ignore punctuation and spaces when matching patterns.|
|`-t`|`--transliterate`|It is used to ignore accents using iconv transliteration when matching patterns.|
|`-l`|`--limit, -n LIMIT`|If this option is specified, the command exit successfully after finding LIMIT entries.|
|`-m`|`--mmap`|It is used to ignore the compatibility with BSD, and GNU locate.|
|`-0`|`--null`|It is used to separate the entries on output using the ASCII NUL character instead of writing each entry on a separate line.|
|`-S`|`--statistics`|It is used to write statistics about each read database to standard output instead of searching for files.|
|`-r`|`--regexp REGEXP`|It is used for searching a basic regexp REGEXP.|
|`--regex`|<center>-</center>|It is used to describe all PATTERNs as extended regular expressions.|
|`-V`|`--version`|It is used to display the version and license information.|
|`-w`|` --wholename`|It is used for matching only the whole path name in specified patterns.|