#!/bin/bash

function printMatrix() {
	# prints out the matrix of all platforms go can target
	echo "darwin 386 
darwin amd64 
darwin arm 
darwin arm64 
dragonfly amd64 
freebsd 386 
freebsd amd64 
freebsd arm 
linux 386 
linux amd64 
linux arm 
linux arm64 
linux ppc64 
linux ppc64le 
netbsd 386 
netbsd amd64 
netbsd arm 
openbsd 386 
openbsd amd64 
openbsd arm 
plan9 386 
plan9 amd64 
solaris amd64 
windows 386 
windows amd64"
}

if [ $1 == "print-matrix" ]
then
	printMatrix
	exit 0
fi

if [ ! -e matrix ]
then
	echo "no 'matrix' file found"
	echo "please run '$0 print-matrix > matrix' and run $0 again."
	exit 1
fi

if [ -z $1 ]
then
	echo "must specify import path of go program to build"
	exit 1
fi

target=$1
name=$(basename $target)
output=${2:-.}

function doBuild() {
	echo ==> building $1 $2
	dir=${output%%/}$1-$2
	mkdir -p $dir
	cd $dir && GOOS=$1 GOARCH=$2 go build $target
}

while read line
do
	doBuild $line
done < matrix

