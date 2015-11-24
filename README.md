# go-buildall
A program to build your go code for every supported platform

## Usage
```bash
# generate initial build matrix
$ buildall print-matrix > matrix

# edit the matrix if you like, remove platforms you dont want to support
$ buildall github.com/you/yourprogram
```
