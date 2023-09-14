### ls  (List command)

lists outs the files in a directory

```bash
ls -l 
```

shows hidden files

```bash
ls -a 
```

display inode numbers for files
```
ls -i
```

display all files recursively
```bash
ls -R
```

see file types
```
ls -F
```

all modifiers can be used in combination
### cp (Copy)

copies all files in a to b (Recursive)

```bash
cp  -R a/ b/ 


```

Asks us to overwrite a file in shell in case there is another file with the same name

```bash
cp  -i 
```


ln (Link files)

```bash
ln file1 file2 'Create hard link'
ln -s file1 file2 'create symbolic link from file 1 to file2'
```

move or rename files
```bash
mv 
```

make new directory
```bash
mkdir
```

make directories and sub-directories
```bash
mkdir -p <dir1/dir2/dir3>
```

remove files
```bash
rm
```

remove empty directories
```bash
rmdir
```

remove files in directory too
```bash
rm  -r
```


remove with caution
```shell
rm -rf
```

view files

```shell
cat <filename>
```

number viewed files
```shell
cat -n
```
number file where text is in line
```shell
cat -b
```

more
less
tail
head